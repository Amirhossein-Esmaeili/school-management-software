# School Management System in Python

This project is a python script for managing school records inside the Terminal. main goal of this project being keeping all data in one place without needing for heavy programs or sql databases. in this system we having 5 main classes: Course, Student, Teacher, Classroom and School.


you working with numbers 1 to 5 inside Terminal menu, and for going back or exit you must writing 0 in Terminal. from root menu you can adding or deleting student, teacher and course. also for deleting course, first code checking all lists and if they having that course it showing this course already use in Terminal.

for checking classroom data you selecting classroom menu in Terminal. in this section system only showing students with score under 10 for that course. I adding this for finding students who needing extra helps fast, so you no need checking every scores one by one.

for saving changes you writing 5 in root menu and save_data method writing all ids and scores inside data4.json file. finally when you opening code again in Terminal, load_data method reading data4.json file and making courses, students, teachers and classrooms automatically.

## Structures

## 1. Class: Course
Represents an academic course in the system.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique numerical identifier for the course |
| `name` | `str` | Name or title of the course |
| `units` | `int` | Number of course credits or units |
| `score` | `float` | The student's grade or score achieved in this course |

---

## 2. Class: Student
Represents a student enrolled in the institution.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique numerical identifier for the student |
| `name` | `str` | Student's first name |
| `family` | `str` | Student's last name |
| `courses` | `list[Course]` | List of courses taken by the student along with their scores |

---

## 3. Class: Teacher
Represents an instructor or teacher.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique numerical identifier for the teacher |
| `name` | `str` | Teacher's first name |
| `family` | `str` | Teacher's last name |
| `grade` | `str` | Teacher's academic degree, rank, or level |
| `courses` | `list[Course]` | List of courses the teacher is qualified to teach |

---

## 4. Class: Classroom
Represents an active class session linking a course, a teacher, and enrolled students.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `int` | Unique numerical identifier for the classroom |
| `name` | `str` | Name or title of the classroom |
| `course` | `Course` | The course being taught in this classroom |
| `teacher` | `Teacher` | The teacher assigned to lead this classroom |
| `students` | `list[Student]` | List of students enrolled in this classroom |

---

## 5. Class: School
The primary management class handling data storage, JSON operations, and navigation context.

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `str` | Name of the school or institution |
| `students` | `list[Student]` | List of all students registered in the school system |
| `teachers` | `list[Teacher]` | List of all teachers working in the school system |
| `courses` | `list[Course]` | List of all courses offered by the school |
| `classrooms` | `list[Classroom]` | List of all classrooms created in the school |
| `selected_student` | `Student` | The student currently selected in the user session |
| `selected_teacher` | `Teacher` | The teacher currently selected in the user session |
| `selected_classroom` | `Classroom` | The classroom currently selected in the user session |