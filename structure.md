<!-- Modellizzare la struttura di una tabella per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. -->

# Università

## Table: Departments (Model: Department)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- name: VARCHAR(50) NOTNULL
- address: VARCHAR(100) NULL
- phone: VARCHAR(16) NOTNULL

## Table: Degrees (Model: Degree)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- department_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- name: VARCHAR(50) NOTNULL
- period: VARCHAR(20) NOTNULL
- description: TEXT NULL

## Table: Courses (Model: Course)

- id: BIGINT NOTNULL (PK, NOTNULL, AI, UNIQUE)
- degree_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- name: VARCHAR(50) NOTNULL
- refrence_code_course: TINYINT

## Table: Teachers (Model: Teacher)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- name: VARCHAR(50) NOTNULL
- lastname: VARCHAR(50) NOTNULL
- phone: VARCHAR(16) NOTNULL
- email: VARCHAR(100) NOTNULL

## Table: Exams (Model: Exam)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- course_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- hour: TIME NOTNULL
- date: DATE NOTNULL
- location: VARCHAR(50) NOTNULL

## Table: Students (Model: Student)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- degree_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- name: VARCHAR(50) NOTNULL
- lastname: VARCHAR(50) NOTNULL
- date_of_birth: DATE
- email: VARCHAR(100) NOTNULL

## Table: Votes (Model: Vote)

- id: BIGINT (PK, NOTNULL, AI, UNIQUE)
- exam_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- student_id: BIGINT (FK, NOTNULL, AI, UNIQUE)
- vote: TINYINT
