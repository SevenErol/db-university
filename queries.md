## Selezionare tutti gli studenti nati nel 1990 (160)

**SELECT * FROM `students` WHERE YEAR (`date_of_birth`) = 1990;**

## Selezionare tutti i corsi che valgono più di 10 crediti (479)

**SELECT * FROM `courses` WHERE `cfu` > 10;**

## Selezionare tutti gli studenti che hanno più di 30 anni

**SELECT * FROM `students` WHERE YEAR(CURDATE()) - YEAR (`date_of_birth`) > 30;**

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

**SELECT * FROM `courses` WHERE `period` = 'I semestre' AND `year` = 1;**

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

**SELECT * FROM `exams` WHERE `date` = '2020/06/20' AND `hour` > '14:00:00';**

## Selezionare tutti i corsi di laurea magistrale (38)

**SELECT * FROM `degrees` WHERE `name` LIKE '%Magistrale%';**

## Da quanti dipartimenti è composta l'università? (12)

**SELECT COUNT(`id`) AS 'Number of departments' FROM `departments`;**

## Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

**SELECT * FROM `teachers` WHERE `phone` IS NULL;**

## GROUP BY SECTION

## Contare quanti iscritti ci sono stati ogni anno

**SELECT COUNT(`students`.`id`), YEAR(`enrolment_date`) FROM `students` GROUP BY YEAR (`enrolment_date`) ORDER BY YEAR (`students`.`enrolment_date`) DESC;**

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

**SELECT COUNT(`teachers`.`id`), `teachers`.`office_address` FROM `teachers` GROUP BY `teachers`.`office_address`;**

## Calcolare la media dei voti di ogni appello d'esame

**SELECT `exam_student`.`exam_id`, AVG(`exam_student`.`vote`) FROM `exam_student` GROUP BY `exam_student`.`exam_id`;**

## Contare quanti corsi di laurea ci sono per ogni dipartimento

**SELECT `degrees`.`department_id`, COUNT(`degrees`.`name`) FROM `degrees` GROUP BY `degrees`.`department_id`;**

## JOIN SECTION


##  Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

**SELECT `students.*`, `degrees`.`name` FROM `students` JOIN `degrees` ON `students`.`degree_id` = `degrees.id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';**

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

**SELECT `degrees`.`name` AS 'Course name',`departments`.`*`  FROM `degrees` JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`WHERE `degrees`.`name` LIKE 'Corso di Laurea Magistrale%' AND `departments`.`name` = 'Dipartimento di Neuroscienze';**

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

**SELECT `teachers`.`id` , `courses`.`*` , `teachers`.`name`, `teachers`.`surname` FROM `course_teacher` JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id` WHERE `teachers`.`id` = 44;**

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

**SELECT `students`.`name` AS 'Name', `students`.`surname` AS 'Surname', `degrees`.`*` ,` departments`.`name` AS 'Department Name' FROM `degrees` JOIN `students` ON `degrees`.`id` = `students`.`degree_id` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` ORDER BY `students`.`surname` ASC, `students`.`name` ASC;**

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

**SELECT `degrees`.`name`,`courses`.`name` AS 'course_name', `teachers`.`name` AS 'teacher_name', `teachers`.`surname` AS 'teacher_surname' FROM `course_teacher` JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id` JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`;**

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

**SELECT DISTINCT `teachers`.`*`, `departments`.`name` AS 'Department_name' FROM `course_teacher` JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id` JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica';**
