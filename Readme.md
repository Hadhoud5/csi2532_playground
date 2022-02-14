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

#### Diagramme ER

Pour chaque situation voici un diagramme ER qui le décrit
(en supposant qu'aucune autre contrainte).

1) Les professeurs peuvent enseigner le même cours sur plusieurs semestres et seule la plus récente doit être enregistrée.

![ER #1](assets/4/1.png)

2) Chaque professeur doit enseigner un cours.

![ER #2](assets/4/2.png)

3) Chaque professeur enseigne exactement un cours (ni plus, ni moins).

![ER #3](assets/4/3.png)

4) Chaque professeur enseigne exactement un cours (ni plus, ni moins), et chaque cours doit être enseigné par un professeur.

![ER #4](assets/4/4.png)

5) Les professeurs peuvent enseigner le même cours sur plusieurs semestres et chaque doit être enregistrée.

![ER #5](assets/4/5.png)

6) Supposons maintenant que certains cours puissent être enseignés conjointement par une équipe de professeurs, mais il est possible qu'aucun professeur dans une équipe ne puisse enseigner le cours. Modélisez cette situation en introduisant des ensembles d'entités et des ensembles de relations supplémentaires si nécessaire.

![ER #6](assets/4/6.png)

#### Diagramme de relation

Avec les diagrammes ER ci-dessus, modèlez un diagramme relationnel pour les systèmes.

1) 
![RD #1](assets/4/7.png)

3) 
![RD #3](assets/4/8.png)

5) 
![RD #5](assets/4/9.png)

6) 
![RD #6](assets/4/10.png)

#### Schèma de relation

Avec les diagrammes relationnel ci-dessus, écrivez un schéma SQL relationnel pour les systèmes.

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
