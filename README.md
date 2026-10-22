# School Management System in Python

## introduction

This project is a python script for managing school records inside the Terminal. main goal of this project being keeping all data in one place without needing for heavy programs or sql databases. in this system we having 5 main classes: Course, Student, Teacher, Classroom and School.


you working with numbers 1 to 5 inside Terminal menu, and for going back or exit you must writing 0 in Terminal. from root menu you can adding or deleting student, teacher and course. also for deleting course, first code checking all lists and if they having that course it showing this course already use in Terminal.

for checking classroom data you selecting classroom menu in Terminal. in this section system only showing students with score under 10 for that course. I adding this for finding students who needing extra helps fast, so you no need checking every scores one by one.

for saving changes you writing 5 in root menu and save_data method writing all ids and scores inside data4.json file. finally when you opening code again in Terminal, load_data method reading data4.json file and making courses, students, teachers and classrooms automatically.

## Structures

## 1. Class: Course

Represents an academic course in the system.

### Properties
| Property | Type | Description | 
| ----- | ----- | ----- | 
| `id` | `int` | Unique numerical identifier for the course | 
| `name` | `str` | Name or title of the course | 
| `units` | `int` | Number of course credits or units | 
| `score` | `float` | The student's grade or score achieved in this course | 

### Methods
| Method | Parameters | Return Type | Description |
| ----- | ----- | ----- | ----- |
| `__init__` | `id, name, units` | `None` | Initializes a new `Course` instance |
| `__eq__` | `other` | `bool` | Compares equality based on course ID |
| `__str__` | None | `str` | Returns formatted string representation (`id`, `name`, `units`) |

---

## 2. Class: Student

Represents a student enrolled in the institution.

### Properties
| Property | Type | Description | 
| ----- | ----- | ----- | 
| `id` | `int` | Unique numerical identifier for the student | 
| `name` | `str` | Student's first name | 
| `family` | `str` | Student's last name | 
| `courses` | `list[Course]` | List of courses taken by the student along with their scores | 

### Methods
| Method | Parameters | Return Type | Description |
| ----- | ----- | ----- | ----- |
| `__init__` | `id, name, family` | `None` | Initializes a new `Student` instance with an empty courses list |
| `__eq__` | `other` | `bool` | Compares student equality by object or ID |
| `__str__` | None | `str` | Returns formatted string representation (`id`, `name`, `family`) |
| `show_info` | None | `None` | Displays student details and their registered courses with scores |
| `add_course` | `course` | `None` | Enrolls student in a course if not already enrolled |
| `remove_course` | `course` | `None` | Removes a registered course from the student's list |
| `set_score` | None | `None` | Prompts user interactive input to set/update grades for enrolled courses |

---

## 3. Class: Teacher

Represents an instructor or teacher.

### Properties
| Property | Type | Description | 
| ----- | ----- | ----- | 
| `id` | `int` | Unique numerical identifier for the teacher | 
| `name` | `str` | Teacher's first name | 
| `family` | `str` | Teacher's last name | 
| `grade` | `str` | Teacher's academic degree, rank, or level | 
| `courses` | `list[Course]` | List of courses the teacher is qualified to teach | 

### Methods
| Method | Parameters | Return Type | Description |
| ----- | ----- | ----- | ----- |
| `__init__` | `id, name, family, grade` | `None` | Initializes a new `Teacher` instance with an empty courses list |
| `__eq__` | `other` | `bool` | Compares teacher equality by object or ID |
| `__str__` | None | `str` | Returns formatted string representation (`id`, `name`, `family`, `grade`) |
| `show_info` | None | `None` | Displays teacher details and their assigned teaching courses |
| `add_course` | `course` | `None` | Assigns a new course capability to the teacher |
| `remove_course` | `course` | `None` | Removes a course assignment from the teacher |

---

## 4. Class: Classroom

Represents an active class session linking a course, a teacher, and enrolled students.

### Properties
| Property | Type | Description | 
| ----- | ----- | ----- | 
| `id` | `int` | Unique numerical identifier for the classroom | 
| `name` | `str` | Name or title of the classroom | 
| `course` | `Course` | The course being taught in this classroom | 
| `teacher` | `Teacher` | The teacher assigned to lead this classroom | 
| `students` | `list[Student]` | List of students enrolled in this classroom | 

### Methods
| Method | Parameters | Return Type | Description |
| ----- | ----- | ----- | ----- |
| `__init__` | `id, name` | `None` | Initializes a new `Classroom` instance |
| `__eq__` | `other` | `bool` | Compares classroom equality by object or ID |
| `__str__` | None | `str` | Returns summary string (`id`, `name`, course, teacher name, student count) |
| `show_info` | None | `None` | Displays classroom information including teacher and enrolled students |
| `change_course` | `all_course` | `None` | Changes class course and filters invalid teacher/students based on new course |
| `change_teacher` | `all_teacher` | `None` | Assigns a qualified teacher (who teaches the class course) to the class |
| `add_student` | `all_student` | `None` | Enrolls a student needing retake (score < 10) into the classroom |
| `remove_student` | None | `None` | Interactively removes a selected student from the classroom |

---

## 5. Class: School

The primary management class handling CRUD operations, interactive selections, and JSON data persistence.

### Properties
| Property | Type | Description | 
| ----- | ----- | ----- | 
| `name` | `str` | Name of the school or institution | 
| `students` | `list[Student]` | List of all students registered in the school system | 
| `teachers` | `list[Teacher]` | List of all teachers working in the school system | 
| `courses` | `list[Course]` | List of all courses offered by the school | 
| `classrooms` | `list[Classroom]` | List of all classrooms created in the school | 
| `selected_student` | `Student` | The student currently selected in the user session | 
| `selected_teacher` | `Teacher` | The teacher currently selected in the user session | 
| `selected_classroom` | `Classroom` | The classroom currently selected in the user session | 

### Methods
| Method | Parameters | Return Type | Description |
| ----- | ----- | ----- | ----- |
| `__init__` | `name` | `None` | Initializes school instance with empty entity collections |
| `add_classroom` | `classroom` | `None` | Adds a new classroom to the school |
| `add_student` | `student` | `None` | Registers a new student in the system |
| `add_teacher` | `teacher` | `None` | Registers a new teacher in the system |
| `add_course` | `course` | `None` | Adds a new course to the curriculum |
| `remove_student` | `student` | `None` | Removes student if not active in any classroom |
| `remove_teacher` | `teacher` | `None` | Removes teacher if not assigned to any active classroom |
| `remove_course` | `course` | `None` | Removes course if not referenced by teachers, students, or classrooms |
| `remove_classroom` | `classroom_id` | `None` | Deletes a classroom by its ID |
| `show_students` | None | `None` | Prints list of all registered students |
| `show_teachers` | None | `None` | Prints list of all registered teachers |
| `show_courses` | None | `None` | Prints list of all offered courses |
| `show_classroom` | None | `None` | Prints list of all existing classrooms |
| `edit_student` | `id, name, family` | `None` | Updates name and family for an existing student |
| `edit_teacher` | `id, name, family, grade` | `None` | Updates details for an existing teacher |
| `edit_courses` | `id, name, units` | `None` | Updates title and units for an existing course |
| `edit_classroom` | `id, name` | `None` | Renames an existing classroom |
| `select_classroom` | `id` | `None` | Sets the active session classroom by ID |
| `load_data` | None | `None` | Loads school data from `data4.json` file |
| `save_data` | None | `None` | Serializes and saves current school state to `data4.json` |

## Structures

### How to use it

When you start the file from the terminal console, the first menu will pop up. Here you can set any number between 0 and 5 to control the entire app. if you then choose number 1 from the menu, it opens course section where you can type to either add a new course name or delete an old ones from the system. but if u want to remove the course that is already assigned to some students or teachers python stops u instantly and prints error message saying that this course is already used so the data connections inside the program can no longer be broken.

It is 2, you directly go into the student menu where you enter student id, first name and last name and then choose from the available list of courses that they study. Then, In 3 you get your teacher menu, almost same thing, where you type in teacher personal info, set their active grade level and then select what courses they teach in school. These are populated in the system memory lists as objects while the program is running.

Classroom is option 4, used as a quick filter to check student performance with fast. One teacher one course, and program will scan entire students in your all student list to show only the ones that got grade under 10 in that course. This feature is very helpful, it immediately shows you which students are failing or might need extra help without having to spend time to manually going through each score here.



so when you press 5 it runs the save_data function to collect all the IDs, names, courses, teachers, classrooms and scores and dumps them all into a data4.json file in the project directory. Then, any time you run the code in terminal, load_data is automatically executed and reads the data4.json file and restores everything so you will never have to type all the data again from the beginning, every time you want to re-run it. To terminate your console safely, all you have to do is type 0, to close the app.