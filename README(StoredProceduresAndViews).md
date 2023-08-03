# GetAttendanceByLessonProgramId Prosedürü
```
USE [SchoolProject]
GO
CREATE OR ALTER PROCEDURE [dbo].[GetAttendanceStatusByStudentId]
    @StudentId INT
AS
BEGIN
    SET NOCOUNT ON;

    SELECT 
        S.Name AS 'Öğrencinin Adı',
	S.Surname AS 'Öğrencinin Soyadı',
        B.Name AS 'Ders Adı',
        LessonTime AS 'Dersin Zamanı',
        IsInClass AS 'Yoklama'
    FROM [dbo].[Attendance] A
	Left Join LessonPrograms L on A.LessonProgramId=L.Id
	Left Join Branches B on L.BranchId=B.Id
	Left Join Students S on A.StudentId=S.Id
    WHERE StudentId = @StudentId;
END
GO
```

**AÇIKLAMA:**  

Bu prosedür, Attendance, LessonPrograms, Branches ve Students tablolarını kullanarak,  
Id'si girilen öğrencinin, derslerindeki devam durumu bilgilerini alabilmek için tasarlanmıştır.  

---

# GetAttendanceStatistics Prosedürü

```
CREATE PROCEDURE [dbo].[GetAttendanceStatistics]
    @StudentName NVARCHAR(50),
    @StudentSurname NVARCHAR(50)
AS
BEGIN
    SET NOCOUNT ON;

    DECLARE @StudentId INT

    -- Öğrencinin Id'sini bulma
    SELECT @StudentId = Id
    FROM dbo.Professions
    WHERE Name = @StudentName AND Surname = @StudentSurname

    IF @StudentId IS NOT NULL
    BEGIN
        -- Öğrencinin katıldığı ders sayısı
        DECLARE @TotalAttendance INT
        SELECT @TotalAttendance = COUNT(*)
        FROM dbo.Attendance
        WHERE StudentId = @StudentId AND IsInClass = 1

        -- Öğrencinin kaçırdığı ders sayısı
        DECLARE @TotalMissed INT
        SELECT @TotalMissed = COUNT(*)
        FROM dbo.Attendance
        WHERE StudentId = @StudentId AND IsInClass = 0

        -- Devamsızlık yüzdesi
        DECLARE @AttendancePercentage FLOAT
        SET @AttendancePercentage = 100.0 * @TotalAttendance / (CASE WHEN @TotalAttendance + @TotalMissed = 0 THEN 1 ELSE @TotalAttendance + @TotalMissed END)

        -- Sonuçları döndürme
        SELECT @StudentName AS StudentName,
               @StudentSurname AS StudentSurname,
               @TotalAttendance AS TotalAttendance,
               @TotalMissed AS TotalMissed,
               @AttendancePercentage AS AttendancePercentage
    END
```

**AÇIKLAMA:**  

Sınıf geçme, taktir ve teşekkür belgelerini alabilme durumlarında kullanmamız gereken önemli bir bilgidir devamsızlık durumu.  
Bundan dolayı her öğrenci için ayrı ayrı girdikleri ders sayısı ve gelemedikleri günlerin sayısı alınarak devam durumlarını yüzdelik hesaplamayla bize verebilecek bir prosedürdür.

---

# GetStudentExams Prosedür

```
CREATE PROCEDURE [dbo].[GetStudentExams]
    @StudentId INT
AS
BEGIN
    SELECT
        E.Id AS ExamId,
        C.Name AS ClassName,
        B.Name AS BranchName,
        E.Name AS ExamName,
        E.Note,
        E.ExamDate,
        E.IsActive
    FROM
        dbo.Exams E
    INNER JOIN
        dbo.Classes C ON E.ClassId = C.Id
    INNER JOIN
        dbo.Branches B ON E.BranchId = B.Id
    WHERE
        E.StudentId = @StudentId;
END
```

**AÇIKLAMA:** 

Sınavların, sınıflara göre, hangi dersten sınava girildiği bilgisini  
ve öğrencilerin bu sınavlardan aldıkları notların bilgisini,  
tarih ve saat belirterek bize verecek olan prosedürdür.

---

# vwStudentAttandenceView

```
    CREATE VIEW [dbo].[vwStudentAttandenceView] AS
	SELECT 
        S.Name AS 'Öğrencinin Adı',
	S.Surname AS 'Öğrencinin Soyadı',
        B.Name AS 'Ders Adı',
        LessonTime AS 'Dersin Zamanı',
        IsInClass AS 'Yoklama'
    FROM [dbo].[Attendance] A
	Left Join LessonPrograms L on A.LessonProgramId=L.Id
	Left Join Branches B on L.BranchId=B.Id
	Left Join Students S on A.StudentId=S.Id
```

**AÇIKLAMA:** 

Bütün öğrencilerin yoklama bilgilerinin bulunduğu sanal tablomuzdur.

---

# vwExamResultsView

```
CREATE VIEW [dbo].[vwExamResultsView] AS
SELECT 
    S.Name AS 'Öğrencinin Adı',
    S.Surname AS 'Öğrencinin Soyadı',
    C.Name AS 'Sınıfı',
    B.Name AS 'Dersi',
    E.Name AS ExamName,
    E.Note AS ExamNote,
    E.ExamDate
FROM Exams E
Left Join Students S ON E.StudentId = S.Id
Left Join Classes C ON E.ClassId=C.Id
Left Join Branches B ON E.BranchId=B.Id
```

**AÇIKLAMA:** 

Öğrencinin adı, soyadı, sınıfı, hangi dersten hangi sınava girdiğini ve notunu gösteren sanal tablodur.

