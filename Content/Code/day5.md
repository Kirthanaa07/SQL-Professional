SQL to create the students_day5 table in your database

```SQL
CREATE TABLE IF NOT EXISTS   students_day5 (
	student_id INT PRIMARY KEY,
	student_name VARCHAR ( 50 )  NOT NULL,
	gpa DECIMAL
);

INSERT INTO  students_day5 (student_id, student_name, gpa) VALUES 
(1, 'john', 2),
(2, 'Rachel', 4),
(3, 'Abe', 3),
(4, 'Joe', 2);
```