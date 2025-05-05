# Experiment 1: Entity-Relationship (ER) Diagram
### Reg No :212223110033
### Nme : OVIYA P

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:
University Database

## ER Diagram:
![image](https://github.com/user-attachments/assets/f05f19b5-3594-4843-9086-1d6f816da36a)


## Entities and Attributes:

### student

1.StudentID(primary key)

2.admission no 

3.name

4.DOB

5.gender

6.Email

7.phone

8.address

### Course

1.course ID(primary key)

2.course name

3.credits

4.department

### Instructor

1.Instructor ID(primary key)

2.name

3.Email

4.phone no

5.deparment

### Deparment

1.Deparment ID(primary key)

2.HOD

3.Department name

### Class

1.class ID(primary key)

2.Semester

3.Year

4.Schedule


## Relationships and Constraints:

Student-Course

1. "Entroll" Relationship
   
2. A student can entroll many course.

Course-Instructor

1. "Faculty" Relationship
   
2. A Instructor can teach one course

Course-Department

1."Offered By" Relationship

2.A course isoffered by one department.

3.A department can offer multiple courses.

Class- Course

 1. "Teaches" Relationship
  
 2. A class is based on one course.
  
 3. A course can have multiple classes


## Extension (Prerequisite / Billing):
- Explain how you modeled prerequisites or billing.

## Design Choices:
Brief explanation of why you chose certain entities, relationships, and assumptions

## RESULT

Thus, The ER Diagram was designed Sucessfully.
