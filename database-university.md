Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d’Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d’Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.diagrams.net/ per la creazione dello schema. Esportare quindi il diagramma in jpg e caricarlo nella repo.



# Tabella Dipartimenti
Id: INT (chiave primaria)
Nome: VARCHAR
Indirizzo: VARCHAR
Email: VARCHAR
Telefono: VARCHAR
Responsabile del dipartimento: VARCHAR
Numero corsi di laurea: INT


# Tabella Corsi di Laurea
Id: INT (chiave primaria)
Nome: VARCHAR
Numero corsi: INT
Codice corso di laurea: VARCHAR
Tipo: VARCHAR
Pre-requisiti: VARCHAR
Responsabile del corso di laurea: VARCHAR
Durata: VARCHAR


# Tabella Corsi
Id: INT (chiave primaria)
Nome: VARCHAR
Esami: VARCHAR
Crediti: INT
Docenti: VARCHAR
Durata: VARCHAR
Studenti: VARCHAR
Descrizione del corso: TEXT
Lingua: VARCHAR

# Tabella Insegnanti
Id: INT (chiave primaria)
Nome: VARCHAR
Cognome: VARCHAR
Anno di nascita: DATE
Email: VARCHAR
Sito web: VARCHAR
Foto: VARCHAR(255)
Materia insegnata: VARCHAR


# Tabella Esami
Id: INT (chiave primaria)
Nome: VARCHAR
Tipo: VARCHAR
Codice: VARCHAR
Data: DATETIME
Aula: VARCHAR
Durata: TIME
Obbligatorio: TINYINT
Crediti: INT

# Tabella Studenti
Id: INT (chiave primaria)
Nome: VARCHAR
Cognome: VARCHAR
Matricola: VARCHAR
Anno di nascita: DATE
Email: VARCHAR
Media voti: FLOAT
Fascia reddituale: VARCHAR
Tipologia Studente: VARCHAR
Data immatricolazione: DATETIME

# Relazioni
-Dipartimenti <OneToMany> Corsi di Laurea
-Corsi di laurea <ManyToMany> Corsi
-Corsi <ManyToMany> Insegnanti
-Corsi di Laurea <ManyToMany> Esame
Studenti <ManyToMany> Corso di laurea 
-Studenti <ManyToMany> Esame

