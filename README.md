# SQL-student-project.

#SQL project : student course system 
 
##Introduction 
        This project uses a sample student management dataset with three tables: 
 
-**Students**-  (student_id,student_name,gender,perc) 
-**courses**  - (course_id,course_name,course_descriptions) 
-**Enrollment** - (e_id,student_id,course_id,e_date) 
 
    The goal is to practice SQL queries and generate student course system.

 ---------
 ##QUERIES##
 
###List all students with their courses 
     SELECT students.student_name, courses.course_name, enrollment.enrollment_date 
FROM students 
JOIN enrollment ON students.student_id = enrollment.student_id 
JOIN courses ON enrollment.course_id = courses.course_id; 

###How many students are in each course 
  SELECT courses.course_name,  
COUNT(enrollment.student_id) AS total_students 
FROM enrollment
JOIN courses ON enrollment.course_id = courses.course_id 
GROUP BY courses.course_name; 
 
###Students not enrolled in any course 
  SELECT students.student_name 
FROM students 
LEFT JOIN enrollment ON students.student_id = enrollment.student_id 
WHERE enrollment.course_id IS NULL; 
 
###Top 3 students by percentage 
  SELECT student_name, percentage 
FROM students 
ORDER BY percentage DESC LIMIT 3; 
