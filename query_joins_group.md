Group by:

# Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(*) AS `student_count`, YEAR(`enrolment_date`)
FROM `students`
GROUP BY YEAR(`enrolment_date`);

# Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS `teachers_count`, `office_address`
FROM `teachers`
GROUP BY `office_address`;

# Calcolare la media dei voti di ogni appello d'esame

SELECT COUNT(`exam_id`) AS `exams_count`, AVG(`vote`) AS `votes_avg` 
FROM `exam_student` 
GROUP BY `exam_id`;

# Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(*) AS `degrees_count`, `department_id` 
FROM `degrees`
GROUP BY `department_id` 
ORDER BY `department_id` ASC;

Joins:
# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`name`, `students`.`surname`, `students`.`registration_number`, `degrees`.`name` AS `degree_name`
FROM `students`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
ORDER BY `registration_number` ASC;

# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` AS `department_name` 
FROM `degrees` 
JOIN `departments` ON `department_id` = `departments`.`id` 
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale';
<!-- risultato= 1; -->

# Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`
FROM `course_teacher`
JOIN `courses` ON `course_id` = `courses`.`id`
JOIN `teachers` ON `teacher_id` = `teachers`.`id`
WHERE `teacher_id` = 44;


# Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name`, `degrees`.`level` AS `degree_level`, `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
JOIN `departments` ON `department_id` = `departments`.`id`
ORDER BY `students`.`name`, `students`.`surname` ASC;


# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`
FROM `course_teacher`
JOIN `courses` ON `course_id` = `courses`.`id`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
JOIN `teachers` ON `teacher_id` = `teachers`.`id`
ORDER BY `degrees`.`name` ASC;


# Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`, `departments`.`name` AS `department_name`
FROM `course_teacher`
JOIN `courses` ON `course_id` = `courses`.`id`
JOIN `degrees` ON `degree_id` = `degrees`.`id`
JOIN `departments` ON `department_id` = `departments`.`id`
JOIN `teachers` ON `teacher_id` = `teachers`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'
ORDER BY `teachers`.`name`, `teachers`.`surname` ASC;

BONUS:
 # Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.