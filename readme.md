# Table Name: University

+ departements:

+ id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ name: VARCHAR(255) | NOTNULL
+ chief: VARCHAR(50) | NOTNULL
+ description: TEXT| NULL
+ degree_course:

+ id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ name: VARCHAR(255) | NOTNULL
+ teachers: SMALLINT | NULL
+ students: SMALLINT | NULL
+ course: TINYINT | NULL
+ description: TEXT| NULL
+ course:

+ id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ name: VARCHAR(255) | NOTNULL
+ teacher: TINYINT | NULL
+ students: SMALLINT | NULL
+ exams: TINYINT | NULL
+ description: TEXT| NULL
+ exam:

+ id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ name: VARCHAR(255) | NOTNULL
+ date: DATE | NULL
+ students: SMALLINT | NULL
+ teacher_id: BIGINT | NOTNULL
+ votes: TINYINT | NOTNULL
+ description: TEXT| NULL
+ teachers:

+ teacher_id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ full_name: VARCHAR(50) | NOTNULL
+ subject: VARCHAR(255) | NOTNULL
+ course: VARCHAR(255) | NULL
+ students:

+ id: BIGINT | AUTO_INCREMENT, UNIQUE, NOTNULL
+ full_name: VARCHAR(50) | NOTNULL
+ degree_course: VARCHAR(255) | NOTNULL
+ course: VARCHAR(255) | NULL
+ exams: VARCHAR(255) | NULL
+ vote: VARCHAR(20) | NULL