# CSI2532

|  |  |
| --- | --- |
| Cours | CSI2532 |
| Date | Hiver 2022 |
| Professor | Dorra Riahi |
| TA | Laith Grira (lgrir057@uottawa.ca) |
| Team | Hedi Ben Abid 300123192 |





## lab004

### Une base de données universitaire

Une base de données universitaire contient des informations sur les professeurs
(identifié par le numéro de sécurité sociale ou SSN) et les cours
(identifié par courseid). Les professeurs donnent des cours; chacun de
les situations suivantes concernent l'ensemble de relation `teaches`.

#### Diagrammes

Pour chaque situation voici un diagramme ER
(en supposant qu'il n'y ait aucune autre contrainte).

1) Les professeurs peuvent enseigner le même cours sur plusieurs semestres et seule la plus récente doit être enregistrée.

<img width="581" alt="1" src="https://user-images.githubusercontent.com/55165009/153781680-f474159f-8fd3-4230-93cc-36f5c8cd1e6a.png">


2) Chaque professeur doit enseigner un cours.

<img width="308" alt="2" src="https://user-images.githubusercontent.com/55165009/153781685-2c8093ac-5b07-43eb-ac30-435dd70ccb71.png">


3) Chaque professeur enseigne exactement un cours (ni plus, ni moins).

<img width="304" alt="3" src="https://user-images.githubusercontent.com/55165009/153781688-08237c31-8c71-40ee-9c4f-3eb75bcb43bc.png">


4) Chaque professeur enseigne exactement un cours (ni plus, ni moins), et chaque cours doit être enseigné par un professeur.

<img width="339" alt="4" src="https://user-images.githubusercontent.com/55165009/153781693-80e7cc38-07a4-4ee2-ad64-92056ed0f8df.png">


5) Les professeurs peuvent enseigner le même cours sur plusieurs semestres et chaque doit être enregistrée.
<img width="713" alt="5" src="https://user-images.githubusercontent.com/55165009/153781695-d73cc0fc-b2af-4495-a5cf-dd58d39e92c3.png">



6) Supposons maintenant que certains cours puissent être enseignés conjointement par une équipe de professeurs, mais il est possible qu'aucun professeur dans une équipe ne puisse enseigner le cours. Modélisez cette situation en introduisant des ensembles d'entités et des ensembles de relations supplémentaires si nécessaire.

<img width="374" alt="6" src="https://user-images.githubusercontent.com/55165009/153781700-b5ea4dd1-c5a8-445c-a81d-212942a99cd9.png">


#### Diagramme de relation

Avec les diagrammes ER ci-dessus, modèlez un diagramme relationnel pour les systèmes.

1) 
![7](https://user-images.githubusercontent.com/55165009/153781701-672e596b-1d5c-438d-96ff-9463b82b7fad.png)


3) 
![8](https://user-images.githubusercontent.com/55165009/153781702-7d8df014-13c5-4d57-918b-eb5cffdf41bd.png)


5) 
![9](https://user-images.githubusercontent.com/55165009/153781704-4d556c61-9fa7-4bc6-ba6f-f644618031a1.png)


6) 
![10](https://user-images.githubusercontent.com/55165009/153781707-7a4a1d35-1b35-4c8c-a909-a2882329be6e.png)


#### Schèma de relation

Avec les diagrammes relationnel ci-dessus, voici un schéma SQL relationnel pour les systèmes.

1) 
```sql
CREATE TABLE "professor" (
  "ssn" varchar(20),
  PRIMARY KEY ("ssn")
);

CREATE TABLE "teaches" (
  "ssn" varchar(20),
  "courseid" varchar(20),
  "semesterid" varchar(20),
  PRIMARY KEY ("ssn", "courseid")
);

CREATE TABLE "course" (
  "courseid" varchar(20),
  PRIMARY KEY ("courseid")
);
```

3) 
```sql
CREATE TABLE "professor" (
  "ssn" varchar(20),
  PRIMARY KEY ("ssn")
);

CREATE TABLE "teaches" (
  "ssn" varchar(20),
  "courseid" varchar(20),
  "semesterid" varchar(20),
  PRIMARY KEY ("courseid")
);

CREATE TABLE "course" (
  "courseid" varchar(20),
  PRIMARY KEY ("courseid")
);


```

5) 
```sql
CREATE TABLE "professor" (
  "ssn" varchar(20),
  PRIMARY KEY ("ssn")
);

CREATE TABLE "teaches" (
  "ssn" varchar(20),
  "courseid" varchar(20),
  "semesterid" varchar(20),
  PRIMARY KEY ("semesterid")
);

CREATE TABLE "course" (
  "courseid" varchar(20),
  PRIMARY KEY ("courseid")
);


```

6) 
```sql
CREATE TABLE "professor" (
  "ssn" varchar(20),
  PRIMARY KEY ("ssn")
);

CREATE TABLE "teaches" (
  "courseid" varchar(20),
  "groupid" varchar(20),
  "semesterid" varchar(20),
  PRIMARY KEY ("semesterid")
);

CREATE TABLE "group" (
  "groupid" varchar(20),
  PRIMARY KEY ("groupid")
);

CREATE TABLE "member_of" (
  "ssn" varchar(20),
  "courseid" varchar(20),
  "membershipid" varchar(20),
  PRIMARY KEY ("membershipid")
);

CREATE TABLE "course" (
  "courseid" varchar(20),
  PRIMARY KEY ("courseid")
);


```
