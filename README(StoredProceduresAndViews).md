# GetAttendanceByLessonProgramId Prosedürü
```
CREATE PROCEDURE [dbo].[GetAttendanceByLessonProgramId]
    @LessonProgramId INT
AS
BEGIN
    SELECT 
        [A].[Id] AS [AttendanceId],
        [A].[LessonProgramId],
        [A].[StudentId],
        [A].[LessonTime],
        [A].[IsInClass],
        [A].[IsActive],
        [S].[Name] AS [StudentName],
        [S].[Surname] AS [StudentSurname]
    FROM [dbo].[Attendance] AS [A]
    INNER JOIN [dbo].[Students] AS [S] ON [A].[StudentId] = [S].[Id]
    WHERE [A].[LessonProgramId] = @LessonProgramId
END
```

**AÇIKLAMA:**  

Bu prosedür, Attendance ve Students tablolarını kullanarak,  
öğrencilerin, belirlediğimiz derslerdeki devam durumlarının bilgilerini alabilmek için tasarlanmıştır.  

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

# vwActiveStudentsView

```
CREATE VIEW [dbo].[vwActiveStudentsView] AS
SELECT Id, Name, Surname, Email, PhoneNumber
FROM Students
WHERE IsActive = 1;
```

**AÇIKLAMA:** 

Öğrencilerin ad-soyad, e-mail ve telefon numaralarının olduğu sanal tablomuzdur.

---

# vwExamResultsView

```
CREATE VIEW [dbo].[vwExamResultsView] AS
SELECT 
    S.Name AS StudentName,
    S.Surname AS StudentSurname,
    E.ClassId,
    E.BranchId,
    E.Name AS ExamName,
    E.Note AS ExamNote,
    E.ExamDate
FROM Exams E
INNER JOIN Students S ON E.StudentId = S.Id;
```

**AÇIKLAMA:** 

Öğrencinin adı, soyadı, sınıfını, hangi branştan hangi sınava girdiğini ve kaç aldığını gösteren bir sanal tablodur.

