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
Id
Nome
Indirizzo
Email
Telefono
Responsabile del dipartimento
Numero corsi di laurea


# Tabella Corsi di Laurea
Id
Nome
Numero corsi
Codice corso di laurea
Tipo
Pre-requisiti
Responsabile del corso di laurea
Durata


# Tabella Corsi
Id
Nome
Esami
Crediti
Docenti
Durata
Studenti
Descrizione del corso
Lingua

# Tabella Insegnanti
Id
Nome
Cognome
Anno di nascita
Email
Sito web
Foto
Materia insegnata


# Tabella Esami
Id
Nome
Tipo
Codice
Data
Aula
Durata
obbligatorio
Crediti

# Table Studenti
Id
Nome
Cognome
Matricola
Anno di nascita
Email
Media voti
Fascia reddituale
Tipologia Studente
Data immatricolazione

# Relazioni
-Dipartimenti <OneToMany> Corsi di Laurea
-Corsi di laurea <ManyToMany> Corsi
-Corsi <ManyToMany> Insegnanti
-Corsi di Laurea <ManyToMany> Esame
Studenti <ManyToMany> Corso di laurea 
-Studenti <ManyToMany> Esame

