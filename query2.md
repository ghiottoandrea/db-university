## Group by

- Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(`enrolment_date`) AS anno, COUNT(*) AS numero_iscritti FROM `students` GROUP BY YEAR(`enrolment_date`);


- Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT `office_address`, COUNT(*) AS 'professori' FROM `teachers` GROUP BY `office_address`;


- Calcolare la media dei voti di ogni appello d'esame

SELECT `exam_id`, AVG(`vote`) AS 'media' FROM `exam_student` GROUP BY `exam_id`;


- Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `department_id`, COUNT(*) AS 'degrees' FROM `degrees` GROUP BY `department_id`;

## Joins

- Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`name`, `students`.`surname`, `students`.`date_of_birth`, `degrees`.`name`
FROM `students` JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';


- Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` FROM `degrees` JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';


- Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `course_teacher`.`course_id`, `courses`.`name`, `courses`.`description` FROM `course_teacher` JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id` WHERE `course_teacher`.`teacher_id` = 44;


- Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`name`, `students`.`surname`, `degrees`.`name`, `degrees`.`level`, `departments`.`name`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`name`, `students`.`surname`;


- Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `courses`.`name` AS 'Nome corso', `courses`.`description` AS 'Descrizione corso',
`teachers`.`name` AS 'Nome professore', `teachers`.`surname` AS 'Cognome professore',
`degrees`.`name` AS 'Nome corso di laurea', `degrees`.`level` AS 'Livello corso di laurea'
FROM `course_teacher`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`


- Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT `teachers`.`name` AS 'Nome professore', `teachers`.`surname` AS 'Cognome professore', `departments`.`name` AS 'Nome dipartimento'
FROM `course_teacher`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'

