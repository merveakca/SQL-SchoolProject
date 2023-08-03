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






