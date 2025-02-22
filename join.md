<!-- 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia -->

SELECT *
FROM `degrees`
JOIN `students` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

<!-- 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze -->

SELECT *
FROM `departments`
JOIN `degrees` ON `degrees`.`department_id`= `departments`.`id`
WHERE `degrees`.`level` = 'MAGISTRALE';

<!-- 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) -->

SELECT *
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id`= 44;

<!-- 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome -->

SELECT `students`.`name`, `students`.`surname`, `degrees`.`name`, `departments`.`name`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`  
ORDER BY `students`.`surname` ASC

<!-- 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti -->

SELECT *
FROM `degrees` 
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`;

<!-- 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54) -->

SELECT *
FROM `teachers` 
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'dipartimento di matematica';

<!-- 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18 -->