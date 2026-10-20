# School Management System in Python

This project is a python script for managing school records inside the Terminal. main goal of this project being keeping all data in one place without needing for heavy programs or sql databases. in this system we having 5 main classes: Course, Student, Teacher, Classroom and School.


you working with numbers 1 to 5 inside Terminal menu, and for going back or exit you must writing 0 in Terminal. from root menu you can adding or deleting student, teacher and course. also for deleting course, first code checking all lists and if they having that course it showing this course already use in Terminal.

for checking classroom data you selecting classroom menu in Terminal. in this section system only showing students with score under 10 for that course. I adding this for finding students who needing extra helps fast, so you no need checking every scores one by one.

for saving changes you writing 5 in root menu and save_data method writing all ids and scores inside data4.json file. finally when you opening code again in Terminal, load_data method reading data4.json file and making courses, students, teachers and classrooms automatically.