# ICT Business Analyst - Aero Club

March - April 2023

> 🔨 Ceci est un labo réalisé chez Technifutur. Il s'agissait d'analyser les processus métiers d'un aéro-club effectuant des réservations de vols libres et qualifiants sans utiliser de système informatique dédié. L'idée était donc de créer un système d'information capable de gérer plus efficacement les réservations de vols et en cas de vol qualifiant, de formateurs.
>
Dans ce repo, vous trouverez les différentes étapes préparatoires et analytiques du projet.
---

**ICT BUSINESS ANALYST**

Les ICT Business Analysts travaillent avec les utilisateurs pour formuler les exigences du système, développer les plans et la documentation du système, examiner et évaluer les systèmes existants, et concevoir et modifier les systèmes pour répondre aux besoins commerciaux des utilisateurs.

Les analystes d'affaires TIC utilisent des techniques de modélisation des données (UML, BPMN...) et des processus pour créer des spécifications de système claires pour la conception et le développement de logiciels de système. Ils constituent une référence centrale et une source d'information, fournissant des conseils et une assistance dans le processus de prise de décision du projet de système.

## Consignes: Laboratoire UML/BPMN : Aéro-club

Avant toute chose, il est nécessaire de bien analyser et comprendre la demande client.
Au besoin, lui demander des précisions si une donnée ou un processus n'est pas compris.

A noter que le rôle du BA est d'apporter une solution à un problème apporté par le client.


````
**Objectifs et consignes**

Réaliser une analyse comprenant :
- le schéma de la base de données (EA et / ou relationnel),
- les BPMN ASIS et TOBE,
- les cas d'utilisations (use cases) avec leurs descriptions textuelles si nécessaires,
- les diagrammes d'activités,
- les diagrammes de classes,
- les diagrammes d’état-transition,
- les différents mockups,
- tout autre modélisation ou explication qui vous semblent pertinentes.

Attention si vous faites des hypothèses sur le cas, celles-ci doivent être indiquées dans l'analyse.

**Outils**

Nous attendons un travail PROFESSIONNEL.

Les applications pouvant êtres utilisés sont:

- Cawemo/Camunda pour le BPMN,
- Looping/Drawio/Mocodo pour les schémas EA / ER,
- StarUML/Visual Paradigme Online pour l’UML,
- Balsamiq Mockup pour les maquettes

**Attendus**

Nous utiliserons une démarche Agile :
- Planifier votre travail avec Trello (inviter votre formateur)
- Chaque jour, nous ferons un Daily Meeting Scrum
- Le dernier jour :
- Présentation de votre travail au matin
- Présentation d’une correction l’après-midi

**Présentation du cas**

Un aéro-club désire structurer les informations qu'il gère sur ses avions et ses pilotes affiliés.
Les avions appartiennent à une catégorie répertoriée d'avions.
Chaque catégorie est repérée par une référence et caractérisée par un descriptif ainsi que par le nombre minimum d'heures de vol d'instruction (vol avec instructeur) nécessaire à la qualification d'un pilote pour cette catégorie.
Chaque avion possède une immatriculation unique. Une description précise de ses équipements de navigation. L'aéro-club fixe également un tarif horaire de location par avion.

À tout moment, on connaît le relevé du compteur horaire de l'avion. On connaît les nom, prénom, adresse et téléphone de chaque pilote. A l'heure actuelle, il n'existe pas deux pilotes ayant le même nom et même prénom. Un pilote peut être qualifié pour un certain nombre de catégories d'avions. Ceci suppose qu'il a volé le nombre d'heures nécessaire à sa qualification. Il peut également être en instruction pour d'autres catégories d'avions. Pour une qualification, on connaît sa date d'obtention et le nombre d'heures de vol effectué en tant que pilote qualifié, pour la catégorie concernée. Pour une instruction, on connaît la date de début et le nombre d'heures de vol effectués pour la catégorie concernée. On connaît aussi le nombre d'heure de vol d'un pilote (toutes catégories
confondues et indépendamment du fait que ces heures sont ou non des heures d'instruction) et le solde de son compte, c'est à dire le montant qu'il doit à l'aéro-club pour des vols qu'il a effectués aux commandes d'un avion.

Un pilote est une personne affiliée au club. Il n'est pas nécessaire d'être qualifié ou en instruction pour une catégorie d'avions pour être considéré comme pilote.
L'aéro-club souhaite également gérer les informations relatives aux vols effectués par ses affiliés.
Pour chaque vol effectué par un pilote aux commandes d'un avion, on enregistre le moment du vol et le compteur horaire de l'avion avant le vol. Pour un avion, un vol est repéré par un numéro d'ordre.
Seul un vol d'instruction, c'est-à-dire avec un instructeur, peut être effectué sur un avion d'une catégorie pour laquelle le pilote aux commandes ne possède pas la qualification. S’il s'agit d'un tel vol, on enregistre également l'instructeur qui accompagne. Un instructeur est un pilote de l'aéro-club, qualifié pour la catégorie à laquelle appartient l'avion utilisé.
Après un vol, on enregistre le nombre d'atterrissages effectués, la valeur du compteur horaire et le coût du vol.

La différence entre les valeurs du compteur horaire avant et après le vol constitue la durée du vol. Celle-ci s'ajoute aux heures de vol du pilote concerné (aucune influence sur le nombre d'heures de vol de l'instructeur).
S'il s'agit d'un vol d'instruction dont la durée est telle que le nombre d'heures d'instruction nécessaire à la qualification du pilote pour la catégorie d'avions concernée est atteint, le pilote est automatiquement enregistré comme étant qualifié pour cette catégorie d'avions. Dans ce cas, la date d'obtention de la qualification correspond à la date du vol en question et le nombre d'heures de vol en tant que pilote qualifié correspond au surplus, par rapport aux nombres d'heures de vol
nécessaires à la qualification, du nombre d'heures de vol d'instruction effectuées pour cette catégorie. Un pilote ne peut être considéré à la fois comme étant qualifié et en instruction par rapport à une catégorie d'avions données.

Le coût d'un vol est obtenu à partir du tarif horaire de location de l'avion et ce l'état de son compteur avant et après le vol. Il est donc indépendant du fait que le vol concerné est ou non un vol d'instruction. Le coût de chaque vol est porté au débitdu compte du pilote aux commandes.
````
_Téléchargement :_ [Consignes- PDF](00-demande-client.pdf)


## 01. Cahier des charges (Specifications)

_Le cahier des charges (souvent abrégé CDC) est un document ou dossier indispensable dans le cadre du développement d'un projet. Il représente un outil de pilotage primordial pour définir les besoins et les spécifications (éléments et règles) liés à un projet._

Ce cahier des charges comprend :

- Cahier des charges
    -  A qui l'application est-elle destinée ?
    -  Quand est-elle attendue ?
    -  Pourquoi est-elle attendue ?
    -  Qu'est-ce qui a motivé la demande ?
    -  Quelles sont les fonctions (besoins fonctionnels)
    -  Quels problèmes doit-elle résoudre ?
    -  Quels sont les bénéfices attendus ?
    -  Quelle sera la portée du système : l'entreprise, un seul service ?
    -  Quelles seront les conditions d'utilisation ?
    -  Comment saura-t-on que l’objectif a été atteint ?
- Les utilisateurs
- BPMN ASIS
- Schéma Entité-Association
- Diagramme de cas d’utilisation
- Diagramme de cas d’utilisation par package
- Scénarii nominaux et alternatifs - Use case – Effectuer un vol à l’aéro-club
    -  Description générale
    1) Scénario nominal / Happy scénario : le pilote est qualifié pour un vol libre
    2) Cas alternatif : le pilote continue une formation
    3) Cas alternatif : le pilote commence une formation
    4) Cas alternatif : le pilote veut réserver un vol libre mais n’a pas la qualification (CTA)
    5) Cas d’exception : le dossier du pilote n’est pas en ordre
- BPMN TOBE
- Diagramme de classes
- Schéma Relationnel
- Glossaire

_Téléchargement :_ [Cahier des charges - PDF](01-specifications_fr.pdf)

## 02. BPMN ASIS

_Le Business Process Model and Notation (BPMN) ou norme de modélisation des processus métier en français, est une méthode de logigramme qui modélise de A à Z les étapes d'un processus métier planifié. L'élaboration et l'alimentation des diagrammes BPMN "As-Is" et "To-Be" sont des techniques efficaces pour transformer une vision en résultats.

Le diagramme "As-Is" offre une vue d'ensemble détaillée de l'état actuel des processus, de la culture et des capacités de l'organisation._

**Réservation d'un vol sans SI**

Dans le cas As-is, tout se fait par téléphone et rien n'est automatisé. Ce qui rend le travail fastdieux pour les opérateurs.

![Diagramme BPMN : Réservation d'un vol sans SI](02-bpmn-asis-reservation.png)

_Téléchargement :_ [Diagramme BPMN : Réservation d'un vol sans SI - Image](02-bpmn-asis-reservation.png)

## 03. BPMN TOBE

_Le diagramme To-Be, fournit une vue d'ensemble de l'état futur, décrivant comment les processus, la culture et les capacités de l'organisation apparaîtront à l'avenir._

L'idée est de créer un SI permettant de gérer différents processus :

- Les interactions avec les membres
- La gestion des membres
- La gestion du personnel
- La réservation des vols
- La gestion de la flotte
- La facturation

Le SI serait disponible pour tous les acteurs de l'aéro-club.

![Organigramme](03h-organizational-chart.png)

**Navigation générale**

![Diagramme BPMN : Navigation générale](03a-bpmn-tobe-site.png)

_Téléchargement :_ [Navigation générale - Image](03a-bpmn-tobe-site.png)

**Dashboard pilote**

![Diagramme BPMN : Dashboard pilote](03b-bpmn-tobe-dashboard.png)

_Téléchargement :_ [Dashboard pilote - Image](03b-bpmn-tobe-dashboard.png)

**Réservation vol libre**

![Diagramme BPMN : Réservation vol libre](03c-bpmn-tobe-reservation-vol-libre.png)

_Téléchargement :_ [Réservation vol libre - Image](03c-bpmn-tobe-reservation-vol-libre.png)

**Réservation vol qualifiant**

![Diagramme BPMN : Réservation vol qualifiant](03d-bpmn-tobe-reservation-vol-qualifiant.png)

_Téléchargement :_ [Réservation vol qualifiant - Image](03d-bpmn-tobe-reservation-vol-qualifiant.png)

**Dashboard formateur**

![Diagramme BPMN : Dashboard formateur](03e-bpmn-tobe-personnel.png)

_Téléchargement :_ [Dashboard formateur - Image](03e-bpmn-tobe-personnel.png)

**Connexion administrateur**

![Diagramme BPMN : xxx](03f-bpmn-tobe-gestion-admin.png)

_Téléchargement :_ [xxx - Image](03f-bpmn-tobe-gestion-admin.png)

**Dashboard administrateur**

![Diagramme BPMN : xxx](03g-bpmn-tobe-gestion-admin-dashboard.png)

_Téléchargement :_ [xxx - Image](03g-bpmn-tobe-gestion-admin-dashboard.png)

## 04. Diagramme entités-associations (Entity Relationship Diagram)

_Un diagramme entité-association est un type d'organigramme illustrant la façon dont des « entités » telles que des personnes, objets ou concepts sont liées les unes aux autres au sein d'un système (cardinalités, héritages...)._

**Schéma Entité-Association**

![Diagramme Entité-Association](04-entity-relationship-diagram.png)

_Téléchargement :_ [Diagramme Entité-Association - Image](04-entity-relationship-diagram.png)

## 05. Shéma relationnel de base de données (Database relational Schema)

_Le schéma relationnel correspond à l'ensemble des relations présentes dans une base de données._

**Schéma Relationnel**

![Schéma Relationnel](05-database-relational-schema.png)

_Téléchargement :_ [Schéma Relationnel - Image](05-database-relational-schema.png)



## 06. UML : diagramme de classes (UML Class Diagram)

_Les diagrammes de classes sont l'un des types de diagrammes UML les plus utiles, car ils décrivent clairement la structure d’un système particulier en modélisant ses classes, ses attributs, ses opérations et les relations (associations) entre ses objets._

**Diagramme de classes**

Ici il reprend les sections supérieure et intermédiaires. A ce stade de l’analyse, les
méthodes (sections inférieures) ne sont pas encore définies.

![UML : Diagramme de classes](06-uml-class-diagram.png)

_Téléchargement :_ [UML : Diagramme de classes - Image](06-uml-class-diagram.png)


## 07. UML : diagramme d'étude de cas d'utilisation (UML Use Cases Diagrams)

_Les diagrammes de cas d'utilisation sont des diagrammes UML utilisés pour une représentation du comportement fonctionnel d'un système logiciel. Ils sont utiles pour des présentations auprès de la direction ou des acteurs d'un projet, mais pour le développement, les cas d'utilisation sont plus appropriés._

**Diagramme de packages de Cas d’utilisation**

![UML Use case : Diagramme de packages de Cas d’utilisation](07a-uml-use-cases-diagram.png)

_Téléchargement :_ [UML Use case : Diagramme de packages de Cas d’utilisation - Image](07a-uml-use-cases-diagram.png)


**Diagramme de cas d’utilisation par package**

![UML Use case : Diagramme de packages de Cas d’utilisation](07b-uml-use-cases-diagram-pakages.png)

_Téléchargement :_ [UML Use case : Diagramme de packages de Cas d’utilisation - Image](07b-uml-use-cases-diagram-pakages.png)

## 10. UML : scenarii d'études de cas d'utilisation (UML Use Cases Scenarii)

_Les documents de scénarios d'utilisation décomposent un processus en décrivant les acteurs, le flux de travail typique mais aussi les choses qui pourraient mal se passer._

Les scenarri concernent :

- 1) Happy scénario : le pilote est qualifié, l’avion est libre
- 2) Cas alternatif : le pilote continue une formation
- 3) Cas alternatif : le pilote commence une formation	3
- 4) Cas alternatif : le pilote veut réserver un vol libre mais n’a pas la qualification (CTA)
- 5) Cas d’exception : le dossier du pilote n’est pas en ordre

_Téléchargement :_ [Scénarii nominaux et alternatifs - PDF](08-uml-use-cases-scenarii.pdf)

## 11. Wireframes

_Le Wireframe est la maquette « fil-de-fer » de l'interface. C'est un schéma de la structure et des fonctionnalités de l'application mobile ou du site. Ces maquettes, dessinées sur du papier ou digitales, présentent un degré d'interactivité variable._

**Le pilote est logué et en ordre de cotisation: il peut accéder à toutes les options**

![Wireframes : Loged ok](11a-wireframes-pilot-loged-ok.png)

_Téléchargement :_ [Wireframes : Loged ok - Image](11a-wireframes-pilot-loged-ok.png)

**Accès au dashboard**

![Wireframes : Dashboard ok](11b-wireframes-pilot-dashboard.png)

_Téléchargement :_ [Wireframes : Dashboard ok - Image](11b-wireframes-pilot-dashboard.png)

![Wireframes : Dashboard ok ](11c-wireframes-pilot-dashboard.png)

_Téléchargement :_ [Wireframes : Dashboard ok - Image](11c-wireframes-pilot-dashboard.png)

![Wireframes : Dashboard ok ](11d-wireframes-pilot-dashboard.png)

_Téléchargement :_ [Wireframes : Dashboard ok - Image](11d-wireframes-pilot-dashboard.png)

![Wireframes : Dashboard ok ](11e-wireframes-pilot-dashboard.png)

_Téléchargement :_ [Wireframes : Dashboard ok - Image](11e-wireframes-pilot-dashboard.png)

**Le pilote est logué mais n'est pas en ordre de cotisation: il ne peut accéder qu'à son dashboard**

![Wireframes : Dashboard ko](11f-wireframes-pilot-loged-ko.png)

_Téléchargement :_ [Wireframes : Dashboard ko- Image](11f-wireframes-pilot-loged-ko.png)

![Wireframes : Dashboard ko](11g-wireframes-pilot-dashboard-ko.png)

_Téléchargement :_ [Wireframes : Dashboard ko - Image](11g-wireframes-pilot-dashboard-ko.png)

**Le pilote est logué et en ordre de cotisation et réserve un avion pour lequel il a le brevet (vol libre)**

![Wireframes : Vol libre](11g-wireframes-pilot-logged-free-flight-choice.png)

_Téléchargement :_ [Wireframes : Vol libre - Image](11g-wireframes-pilot-logged-free-flight-choice.png)

![Wireframes : Vol libre](11h-wireframes-pilot-logged-free-flight-date-hour.png)

_Téléchargement :_ [Wireframes : Vol libre  Image](11h-wireframes-pilot-logged-free-flight-date-hour.png)

![Wireframes : Vol libre](11i-wireframes-pilot-logged-free-flight-recap.png)

_Téléchargement :_ [Wireframes : Vol libre - Image](11i-wireframes-pilot-logged-free-flight-recap.png)

![Wireframes : Vol libre](11j-wireframes-pilot-logged-free-flight-pay.png)

_Téléchargement :_ [Wireframes : Vol libre - Image](11j-wireframes-pilot-logged-free-flight-pay.png)

![Wireframes : Vol libre](11k-wireframes-pilot-logged-free-flight-pay-ok.png)

_Téléchargement :_ [Wireframes : Vol libre - Image](11k-wireframes-pilot-logged-free-flight-pay-ok.png)

**Le pilote est logué et en ordre de cotisation et continue une formation entamée (vol qualifiant)**

![Wireframes : Vol qualifiant en cours](11l-wireframes-pilot-logged-free-flight-choice-training.png)

_Téléchargement :_ [Wireframes : Vol qualifiant en cours - Image](11l-wireframes-pilot-logged-free-flight-choice-training.png)

![Wireframes : Vol qualifiant en cours](11m-wireframes-pilot-logged-free-flight-choice-training-instructor.png)

_Téléchargement :_ [Wireframes : Vol qualifiant en cours - Image](11m-wireframes-pilot-logged-free-flight-choice-training-instructor.png)

![Wireframes : Vol qualifiant en cours](11n-wireframes-pilot-logged-free-flight-choice-training-recap.png)

_Téléchargement :_ [Wireframes : Vol qualifiant en cours - Image](11n-wireframes-pilot-logged-free-flight-choice-training-recap.png)

**Le pilote est logué et en ordre de cotisation mais n'a pas de brevet pour un vol libre et veut choisir un vol qualifiant alors qu'il en suit déjà un autre**

![Wireframes : Vol qualifiant en cours](11o-wireframes-pilot-logged-free-flight-full.png)

_Téléchargement :_ [Wireframes : Vol qualifiant en cours - Image](11o-wireframes-pilot-logged-free-flight-full.png)

**Le pilote est logué et en ordre de cotisation mais, soit n'est pas qualifié pour voler seul, soit désire passer le brevet pour une autre catégorie d'appareils**

Il est invité à faire un choix de type d'avion et à réserver un vol avec un formateur.

![Wireframes : Nouveau vol qualifiant](11p-wireframes-pilot-logged-free-flight-choice.png)

_Téléchargement :_ [Wireframes : Nouveau vol qualifiant - Image](11p-wireframes-pilot-logged-free-flight-choice.png)

![Wireframes : Nouveau vol qualifiant](11q-wireframes-pilot-logged-free-flight-choicenew-training.png)

_Téléchargement :_ [Wireframes : Nouveau vol qualifiant - Image](11q-wireframes-pilot-logged-free-flight-choicenew-training.png)

![Wireframes : Nouveau vol qualifiant](11r-wireframes-pilot-logged-free-flight-choicenew-training-plane.png)

_Téléchargement :_ [Wireframes : Nouveau vol qualifiant - Image](11r-wireframes-pilot-logged-free-flight-choicenew-training-plane.png)

**Dashboard d'un formateur**

permet de consulter le planning, d'éditer ses coordonnées...

![Wireframes : Dashboard formateur](11s-wireframes-formateur-dash-coord.png)

_Téléchargement :_ [Wireframes : Dashboard formateur - Image](11s-wireframes-formateur-dash-coord.png)

![Wireframes : Dashboard formateur](11t-wireframes-formateur-dash-coord-planning.png)

_Téléchargement :_ [Wireframes : Dashboard formateur - Image](11t-wireframes-formateur-dash-coord-planning.png)

![Wireframes : Dashboard formateur](11u-wireframes-formateur-dash-coord-planning-2.png)

_Téléchargement :_ [Wireframes : Dashboard formateur - Image](11u-wireframes-formateur-dash-coord-planning-2.png)

![Wireframes : Dashboard formateur](11v-formateur-dash-documents.png)

_Téléchargement :_ [Wireframes : Dashboard formateur - Image](11v-formateur-dash-documents.png)

**Dashboard d'un GRH / Administrateur**

Permet de gérer les formateurs, la flotte, la compta...

![Wireframes : Dashboard grh](12a-wireframes-admin-dash-coord.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12a-wireframes-admin-dash-coord.png)

![Wireframes : Dashboard grh](12b-wireframes-admin-dash-coordadmin-dash-flotte.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12b-wireframes-admin-dash-coordadmin-dash-flotte.png)

![Wireframes : Dashboard grh](12c-wireframes-admin-dash-coordadmin-dash-cat-edit.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12c-wireframes-admin-dash-coordadmin-dash-cat-edit.png)

![Wireframes : Dashboard grh](12d-wireframes-admin-dash-coordadmin-dash-add-trainer.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12d-wireframes-admin-dash-coordadmin-dash-add-trainer.png)

![Wireframes : Dashboard grh](12f-wireframes-admin-dash-coord.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12f-wireframes-admin-dash-coord.png)

![Wireframes : Dashboard grh](12g-wireframes-admin-dash-coordadmin-dash-planning.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12g-wireframes-admin-dash-coordadmin-dash-planning.png)

![Wireframes : Dashboard grh](12h-wireframes-admin-dash-coordadmin-dash-grh.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12h-wireframes-admin-dash-coordadmin-dash-grh.png)

![Wireframes : Dashboard grh](12i-wireframes-admin-dash-coordadmin-dash-compta.png)

_Téléchargement :_ [Wireframes : Dashboard grh - Image](12i-wireframes-admin-dash-coordadmin-dash-compta.png)


-----------------------------------------------