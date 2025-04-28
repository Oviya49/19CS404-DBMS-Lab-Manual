# ER Diagram Submission - Oviya N

## Scenario Chosen:
## University  

## ER Diagram:
![image](https://github.com/user-attachments/assets/e13200c3-547c-4483-93b1-bca725c2bc37)


## Entities and Attributes:
### 1.Student:
```
->StudentID (Primary Key)
->Name
->DOB
->ContactInfo
->PhoneNo
->Email
```
### 2.Programs:
```
->ProgramID (Primary Key)
->ProgramName
->Department
```
### 3.Courses:
```
->CourseID (Primary Key)
->CourseName
->Credits
->Units
```
### 4.Professors:
```
->ProfessorID (Primary Key)
->Name
->DOB
->ContactInfo
->PhoneNo
->Email
```
### 5.Enrollment (Associative Entity):
```
->CourseID (Foreign Key)
->CourseName
->Date
```
### 6.Prerequisites:
```
->CourseID (Primary Key)
->Name
->Credits
->Units
->PrereqCourseID
->PrereqCourseName
```
## Relationships and Constraints:

### 1.Programs - Student:
```
->1 Program has many Students (1:N).
->Participation: Total on Student side (each Student must be enrolled in a Program).
```
### 2.Student - Enrollment:
```
->1 Student can do many Enrollments (1:N).
->Participation: Partial (A Student might not yet enroll in any course.)
```
### 3.Enrollment - Courses:
```
->Many Enrollments are associated with one Course (N:1).
->Participation: Total on Enrollment side.
```
### 4.Courses - Professors:
```
->1 Course can be taken by 1 Professor.
->1 Professor can teach many Courses (1:N).
->Participation: Partial on Professor side (a Professor may not teach any course yet.)
```
### 5.Courses - Prerequisites:
```
->1 Course can have zero or more Prerequisite Courses (1:N).
->Participation: Partial on Course side (Prerequisite is optional.)
```
## Extension (Prerequisite / Billing):
### 1.Prerequisite Modeling:
```
->You created a separate Prerequisites entity that maps a Course to its Prerequisite Course using:
->CourseID and PrereqCourseID.
->This allows a course to have zero, one, or multiple prerequisites.
```
### 2.Billing:
```
->Billing is not modeled directly in your diagram.
->(If needed, you could add a Billing entity linked to StudentID later.)
```
## Design Choices:
```
->Programs entity was added to group Students under a department/program.
->Used Enrollment as an associative entity because there is a many-to-many relationship between Students and Courses, and Enrollment captures the extra attribute Date (when they enrolled).
->Prerequisites were separated as an independent entity rather than recursive relationship for clarity, making it easier to store additional details about prerequisite courses.
->Contact Information (PhoneNo and Email) was stored under ContactInfo attribute group to avoid redundancy across Student and Professor entities.
->Assumed:
->Each Course can have multiple Students enrolled.
->Each Course can be taught by only one Professor at a time.
->Students must be enrolled in a Program but not necessarily enrolled in a Course immediately.
```
