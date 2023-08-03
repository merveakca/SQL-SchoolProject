# GetAttendanceByStudentId Prosedürü
```
CREATE OR ALTER PROCEDURE [dbo].[GetAttendanceByStudentId]
    @StudentId INT
AS
BEGIN
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
```

**AÇIKLAMA:**  

Bu prosedür, Attendance, LessonPrograms, Branches ve Students tablolarını kullanarak,  
Id'si girilen öğrencinin, derslerindeki devam durumu bilgilerini alabilmek için tasarlanmıştır.  

---

# AddStudent Prosedürü

```
CREATE PROCEDURE [dbo].[AddStudent]
	@LevelId int,
	@ClassId int,
	@Name nvarchar(50),
	@Surname nvarchar(50),
	@Email nvarchar(50),
	@PhoneNumber nvarchar(50),
	@MotherName nvarchar(50),
	@FatherName nvarchar(50),
	@ParentPhoneNumber nvarchar(50),
	@CreatedProfessionId int,
	@UpdatedProfessionId int
AS
BEGIN
	Insert Into Students Values(@LevelId,@ClassId,@Name,@Surname,@Email,@PhoneNumber,@MotherName,@FatherName,
	@ParentPhoneNumber,1,@CreatedProfessionId,GETDATE(),@UpdatedProfessionId,GETDATE())
END
```

**AÇIKLAMA:**  

Yeni öğrenci ekleyen bir prosedürdür.

---

# GetStudentExams Prosedür

```
CREATE PROCEDURE [dbo].[GetStudentExams]
    @StudentId INT
AS
BEGIN
    SELECT
	S.Name AS 'Öğrencinin Adı',
	S.Surname AS 'Öğrencinin Soyadı',
        C.Name AS 'Sınıfı',
        B.Name AS 'Dersi',
        E.Name AS 'Sınavı',
        E.Note AS 'Sınav Notu',
        E.ExamDate 'Sınav Tarihi'
    FROM Exams E
	LEFT JOIN Classes C ON E.ClassId = C.Id
	LEFT JOIN Branches B ON E.BranchId = B.Id
	LEFT JOIN Students S ON E.StudentId=S.Id
    WHERE E.StudentId = @StudentId;
END
```

**AÇIKLAMA:** 

Id'si girilen öğrencinin bütün sınav notlarını gösteren prosedürdür.

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

