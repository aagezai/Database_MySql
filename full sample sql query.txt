CREATE TABLE student(
    student_id INT AUTO_INCREMENT,
    name VARCHAR(20) NOT NULL,
    major VARCHAR(20) DEFAULT 'UNDISIDED',
      gpa DECIMAL(3,2),
    PRIMARY KEY(student_id)
);

-- alter a table to add a column 
ALTER TABLE student ADD gpa DECIMAL(3,2);
-- insert a table specifing the columns 
INSERT INTO student (name,major,gpa) VALUES("ABRAHA",'CHEMISTRY',2);
INSERT INTO student(name,major,gpa) VALUES ("AARON","BIOLOGY",3);
-- alter a table to drop a column
ALTER TABLE student DROP column gpa;
-- to show all data type of the table
Describe student;
-- select order-by and limt
SELECT * 
FROM student
WHERE major ='BIOLOGY'
ORDER BY GPA 
LIMIT 1;
-- drop a table 
DROP TABLE student;
-- CHANGE MYSQL TO FROM SAFE UPDATE TO UNSAFE
SET SQL_SAFE_UPDATES = 0;
-- update a student's attribute data
UPDATE student 
SET major ='Math'
WHERE major ='BIOLOGY';
-- OR
UPDATE student 
SET major ='Mathematics'
WHERE student_id=1;
-- or 
UPDATE student 
SET major ='Math',gpa =2
WHERE  student_id=1;
-- delete row from a table 
DELETE
FROM student
WHERE name ='Aaron';
-- display entire table 
select * from  student;
-- or for specific column 
SELECT name from student;
SELECT student.name FROM student;
-- OR DESCNDING select
SELECT s.name, s.major
FROM student s ORDER BY s.major,s.gpa DESC ;
-- Filter select using or and > < and key-words
SELECT s.name, s.major 
FROM student s
WHERE major ='CHEMISTRY' OR major ='biology' and s.gpa >2;
-- SELECT AND IN 
SELECT s.name, s.major
FROM student s 
WHERE s.major IN ('CHEMISTRY','BIO') AND s.gpa >2;
-- sub query to use IN
SELECT s.name, s.major
FROM student s 
WHERE s.major 
IN (select major from student) -- over here we are getting the list of major
AND s.gpa >2;