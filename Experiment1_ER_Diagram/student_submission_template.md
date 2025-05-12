## Experiment 1: Entity-Relationship (ER) Diagram
## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.
## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

*User Requirements:*
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

*User Requirements:*
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---
## 📝 Tasks:
1.Identify entities, relationships, and attributes.
2.Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3.Include:
* Cardinality & participation constraints
* Prerequisites for University OR Billing for Hospital
4.Explain:
* Why you chose the entities and relationships.
* How you modeled prerequisites or billing.
# ER Diagram Submission - Oviya N

## Scenario Chosen: University  

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
## Result:
Thus, the Entity-Relationship (ER) Diagram have been created successfully.



