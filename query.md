- Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * FROM `students` WHERE date_of_birth LIKE '1990-%';
SELECT * FROM `students` WHERE YEAR(`data_of_birth`) = 1990;


- Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * FROM `courses` WHERE cfu > 10;


- Selezionare tutti gli studenti che hanno più di 30 anni

SELECT * FROM `students` WHERE date_of_birth NOT BETWEEN '1994-01-01' and '2024-01-01'; `SBAGLIATA`
SELECT * FROM `students` WHERE date_of_birth < DATE_SUB(NOW(), INTERVAL 30 YEAR);
SELECT * FROM `students` WHERE TIMESTAMPDIFF(YEAR, date_of_birth, CURDATE()) >= 30;


- Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT * FROM `courses` WHERE period = 'I semestre' and year = 1;

- Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT * FROM `exams` WHERE hour > '14:00' and date LIKE '2020-06-20';
SELECT * FROM `exams` WHERE date = '2020-06-20' AND HOUR(`hour`) >= 14;


- Selezionare tutti i corsi di laurea magistrale (38)

SELECT * FROM `degrees` WHERE level = 'magistrale';


- Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(*) AS total_department FROM `departments`;


- Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(*) AS teachers_with_no_phone FROM `teachers` WHERE phone IS NULL;
