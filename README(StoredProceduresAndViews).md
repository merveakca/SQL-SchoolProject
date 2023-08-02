

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
