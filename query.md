- Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * FROM `students` WHERE date_of_birth LIKE '1990-%';


- Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * FROM `courses` WHERE cfu > 10;


- Selezionare tutti gli studenti che hanno più di 30 anni

SELECT * FROM `students` WHERE date_of_birth NOT BETWEEN '1994-01-01' and '2024-01-01';


- Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT * FROM `courses` WHERE period LIKE 'I %' and year = 1;


- Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT * FROM `exams` WHERE hour > '14:00' and date LIKE '2020-06-20';


- Selezionare tutti i corsi di laurea magistrale (38)

SELECT * FROM `degrees` WHERE level LIKE 'magi%';


- Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(*) AS total_department FROM `departments`;


- Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(*) AS teachers_with_no_phone FROM `teachers` WHERE phone IS NULL;