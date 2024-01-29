## SchoolDb Project
#SQL Homework 

![image](https://github.com/caglatunc/Okul-Projesi-Database-Tasarimi/assets/95507765/6d7d7d15-c10d-4c2b-b665-2a1ad0a4f417)

The Users table contains general information for individuals associated with the school (Students, Teachers, Principals, etc.).
1) [Id]: Each user is assigned a unique identifier (UserID).
2) [Name]: This field stores the user's name and surname information.
3) [Email]: This field stores the user's email address.
4) [PhoneNumber]: This field stores the user's phone number.

``` SQL
CREATE TABLE [dbo].[Users](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](50) NOT NULL,
	[Email] [varchar](50) NOT NULL,
	[PhoneNumber] [varchar](20) NOT NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```

The Students table contains details related to students.
1) [UserId]: Associated with the UserId field in the Users table.
2) [ParentsContactInfo]: Stores the contact information of the student's parents.
3) [ClassId]: Stores the ID of the class the student is enrolled in.
4) [DepartmentId]: Stores the identity of the department the student is enrolled in.

```SQL 
CREATE TABLE [dbo].[Students](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[UserId] [int] NOT NULL,
	[ParentsContactInfo] [varchar](100) NOT NULL,
	[ClassId] [int] NOT NULL,
	[DepartmentId] [int] NOT NULL,
 CONSTRAINT [PK_Students] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```

The Courses table contains details related to courses.
1) [Id]: Each course is assigned a unique identifier.
2) [Name]: Used to store the name of the course.
3) [TeacherId]: Used to store the identity of the teacher assigned to the course.

```SQL 
CREATE TABLE [dbo].[Courses](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](100) NOT NULL,
	[TeacherId] [int] NOT NULL,
 CONSTRAINT [PK_Courses] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
````
The ExamTypes table contains types of exams.
1) [Id]: A unique identifier (UserID) is assigned to each type of exam.
2) [ExamTypeName]: Used to store the names of exam types.
   
````SQL
CREATE TABLE [dbo].[ExamTypes](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[ExamTypeName] [varchar](50) NOT NULL,
 CONSTRAINT [PK_ExamTypes] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
`````

The Exams table contains information about the exams conducted.
1) [Id]: A unique identifier is assigned to each exam.
2) [CoursesId]: Used to specify the course associated with the exam.
3) [ExamDate]: Used to store the date of the exam.
4) [ExamTypesId]: Used to specify the type of exam.
 
````SQL
CREATE TABLE [dbo].[Exams](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[CoursesId] [int] NOT NULL,
	[ExamDate] [date] NOT NULL,
	[ExamTypesId] [int] NOT NULL,
 CONSTRAINT [PK_Exams] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
````
The ExamResults table contains the results of the exams taken.
1) [Id]: A unique identifier is assigned to each exam result.
2) [StudentId]: Used to specify which student the exam result belongs to.
3) [ExamId]: Used to specify which exam the result belongs to.
4) [Grade]: Used to store the grade received by the student.

```SQL
CREATE TABLE [dbo].[ExamResults](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[StudentId] [int] NOT NULL,
	[ExamId] [int] NOT NULL,
	[Grade] [int] NOT NULL,
 CONSTRAINT [PK_ExamResults] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The Classes table contains the names of the classes in the school (e.g., Prep, Class 1, etc.).
1) [Id]: Used to assign a unique identifier to each class.
2) [Name]: Used to store the name of the class.

```SQL
CREATE TABLE [dbo].[Classes](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](100) NOT NULL,
 CONSTRAINT [PK_Classes] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The Department's table contains the names of the departments in the school.
1) [Id]: Used to assign a unique identifier to each department.
2) [Name]: Used to store the name of the department.


```SQL
CREATE TABLE [dbo].[Departments](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](100) NOT NULL,
 CONSTRAINT [PK_Departments] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The StudentTranscripts table contains the transcript information of students.
1) [Id]: Used to assign a unique identifier to each student transcript.
2) [StudentId]: Used to specify which student the transcript belongs to.
3) [CourseId]: Used to specify which course the transcript is related to.
4) [MidtermGrade]: Used to store the midterm grade of the student.
5) [FinalGrade]: Used to store the final grade of the student.
6) [OverallGrade]: Used to store the overall grade of the student in the course.

```SQL
CREATE TABLE [dbo].[StudentTranscripts](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[StudentId] [int] NOT NULL,
	[CourseId] [int] NOT NULL,
	[MidtermGrade] [int] NOT NULL,
	[FinalGrade] [int] NOT NULL,
	[OverallGrade] [float] NOT NULL,
 CONSTRAINT [PK_StudentTranscripts] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The Assistant Principal's table contains information about the assistant principals.
1) [Id]: Used to assign a unique identifier to each assistant principal.
2) [UserId]: Used to specify the user ID of the assistant principal.

```SQL
CREATE TABLE [dbo].[AssistantPrincipals](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[UserId] [int] NOT NULL,
 CONSTRAINT [PK_AssistantPrincipals] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```

The Attendances table contains information about student attendance statuses.
1) [Id]: Used to assign a unique identifier to each attendance record.
2) [StudentId]: Used to specify which student the attendance status belongs to.
3) [Date]: Used to store the date of the attendance.
4) [StatusId]: Used to specify the attendance status.

```SQL
CREATE TABLE [dbo].[Attendances](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[StudentId] [int] NOT NULL,
	[Date] [date] NOT NULL,
	[StatusId] [int] NOT NULL,
 CONSTRAINT [PK_Attendances] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
```
The AttendanceStatus table contains descriptions of attendance statuses.
1) [Id]: Used to assign a unique identifier to each attendance status.
2) [Name]: Used to store the names of attendance statuses such as "Present" or "Absent".

```SQL
CREATE TABLE [dbo].[AttendanceStatus](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Name] [varchar](10) NOT NULL,
 CONSTRAINT [PK_AttendanceStatus] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The Principals table contains information about the principals in the school.
1) [Id]: Used to assign a unique identifier to each principal.
2) [UserId]: Used to specify the user ID of the principal.

```SQL
CREATE TABLE [dbo].[Principals](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[UserId] [int] NOT NULL,
 CONSTRAINT [PK_Principals] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The Teachers table contains information about the teachers in the school.
1) [Id]: Used to assign a unique identifier to each teacher.
2) [UserId]: Used to specify the user ID of the teacher.
3) [Department]: Used to specify the department in which the teacher works.

```SQL
CREATE TABLE [dbo].[Teachers](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[UserId] [int] NOT NULL,
	[Department] [varchar](50) NOT NULL,
 CONSTRAINT [PK_Teachers] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
```
The GetStudentExamResults Stored Procedure is used to retrieve the exam results of a specified student from the database.
With a single call, the exam results of a specific student can be obtained.

For example, to retrieve the exam results of a student named "Cagla Tunc," you can call this procedure as follows: EXEC GetStudentExamResults 'Cagla Tunc'; This eliminates the need to repeatedly write a detailed query.

```SQL
ALTER PROCEDURE [dbo].[GetStudentExamResults]
      @StudentName varchar(50)
AS
BEGIN
		SELECT u.Name as StudentName, c.Name as CourseName,e.ExamDate, et.ExamTypeName, er.Grade as AverageGrade
		from Exams e

		INNER JOIN Courses c on e.CoursesId = c.Id
		INNER JOIN ExamResults er on e.Id= er.ExamId
		INNER JOIN ExamTypes et ON e.ExamTypesId = et.Id
		INNER JOIN Students s ON  er.StudentId = s.Id
		INNER JOIN Users u on s.UserId=u.Id
		WHERE  u.Name = @StudentName
END
```
An AllStudentExamResultsView has been created as a view. This view presents detailed information about students' exam results in the database. 
Using this view, you can access the exam results of desired students with a single query without the need to repeatedly query or merge the data.

For example, to retrieve the exam results of a student named "Cagla Tunc," you can assign a query to the view as follows: SELECT * FROM AllStudentExamResultsView WHERE StudentName = 'Cagla Tunc';
This query provides access to the exam results of the specified student without the need for additional joins or queries.

```SQL
ALTER VIEW [dbo].[AllStudentExamResultsView] AS


SELECT u.Name as StudentName, c.Name as CourseName,e.ExamDate, et.ExamTypeName, er.Grade as Grades
		from Exams e

		INNER JOIN Courses c on e.CoursesId = c.Id
		INNER JOIN ExamResults er on e.Id= er.ExamId
		INNER JOIN ExamTypes et ON e.ExamTypesId = et.Id
		INNER JOIN Students s ON  er.StudentId = s.Id
		INNER JOIN Users u on s.UserId=u.Id
```
