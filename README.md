# Outil-Edition-Questions-Ouvertes
Application desktop JavaFX pour la gestion, la consultation et l’évaluation de questions ouvertes.

<h1 align="center"><strong>Outil d’édition de questions ouvertes</strong></h1>
<h3 align="center">Application desktop JavaFX pour la gestion, la consultation et l’évaluation de questions ouvertes</h3>

<p align="center">
  <strong>Auteurs :</strong> POPESCU Ana-Ioana & OLARU Livia &nbsp;|&nbsp;
  <strong>Groupe :</strong> 1231FA &nbsp;|&nbsp;
  <strong>Université :</strong> Université Nationale de Science et Technologie POLITEHNICA Bucarest &nbsp;|&nbsp;
  <strong>Faculté :</strong> Faculté d’Ingénierie en Langues Étrangères
</p>

---

## TABLE DES MATIÈRES

- [DESCRIPTION](#description)
- [ACTEURS DU SYSTÈME](#acteurs-du-système)
- [FONCTIONNALITÉS PRINCIPALES](#fonctionnalités-principales)
- [ARCHITECTURE](#architecture)
- [COMPOSANTES LOGICIELLES](#composantes-logicielles)
- [RÈGLES MÉTIER](#règles-métier)
- [TECHNOLOGIES ET BIBLIOTHÈQUES](#technologies-et-bibliothèques)
- [ORGANISATION DU PROJET](#organisation-du-projet)

---

## DESCRIPTION

[cite_start]Le projet **« Outil d’édition de questions ouvertes »** consiste en le développement d’une application desktop réalisée en **JavaFX**[cite: 1, 62]. Son objectif est de moderniser et d'optimiser le processus de création pédagogique et d'évaluation. [cite_start]L'application permet aux enseignants de concevoir des questions ouvertes complexes, de les organiser en tests, et d'évaluer les soumissions des étudiants de manière structurée[cite: 6, 7, 11, 28].

---

## ACTEURS DU SYSTÈME

* [cite_start]**Étudiant** : Il crée son compte, consulte les tests publiés, soumet ses réponses aux questions ouvertes et visualise ses notes ainsi que les feedbacks reçus[cite: 5, 11, 15, 71, 75].
* **Enseignant** : Acteur principal de la création de contenu. [cite_start]Il conçoit les questions, organise les tests, publie le matériel pédagogique et évalue les réponses des étudiants[cite: 6, 7, 84, 87].
* [cite_start]**Administrateur** : Il assure la gestion des utilisateurs, valide les comptes des enseignants et peut supprimer des comptes pour maintenir l'intégrité de la plateforme[cite: 63, 65, 68].

---

## FONCTIONNALITÉS PRINCIPALES

### Fonctionnalités de l'Enseignant
- [cite_start]**Gestion des Questions** : Création et modification de questions avec titre, énoncé, niveau de difficulté et score maximum[cite: 6, 90].
- [cite_start]**Organisation des Tests** : Regroupement de questions dans des tests spécifiques et gestion de leur publication[cite: 7, 85, 87].
- [cite_start]**Évaluation** : Consultation des réponses soumises, ajout de feedback (commentaires) et attribution de notes finales[cite: 4, 8, 25, 80, 83].

### Fonctionnalités de l'Étudiant
- [cite_start]**Participation** : Consultation des tests publiés et rédaction des réponses[cite: 69, 71, 72].
- [cite_start]**Suivi** : Consultation des résultats obtenus et lecture des feedbacks de l'enseignant[cite: 11, 75].

---

## ARCHITECTURE

[cite_start]L'application suit une architecture **MVC (Model-View-Controller)** pour garantir une séparation claire entre l'interface utilisateur, la logique métier et l'accès aux données[cite: 176].

### Organisation Modulaire
- [cite_start]**Interface Utilisateur** : Définie par des fichiers FXML et stylisée avec CSS[cite: 171, 176].
- [cite_start]**Contrôleurs** : Gèrent les interactions entre la vue et les services (ex: `QuestionController`, `AuthController`)[cite: 46, 176].
- [cite_start]**Services Métier** : Implémentent la logique applicative (ex: `QuestionService`, `AuthService`)[cite: 136, 176].
- [cite_start]**Accès aux Données (DAO)** : Gère la persistance des informations dans la base de données via JDBC[cite: 55, 176].

---

## COMPOSANTES LOGICIELLES

| Couche | Rôle | Exemples |
| :--- | :--- | :--- |
| **View** | Interface graphique et interaction | [cite_start]`QuestionView`, `LoginView`, `DashboardView` [cite: 161, 171] |
| **Controller** | Coordination et traitement des actions | [cite_start]`QuestionController`, `AuthController`, `EvaluationController` [cite: 167, 168, 169] |
| **Service** | Logique métier et validation | [cite_start]`QuestionService`, `AuthService`, `EvaluationService` [cite: 164, 166] |
| **Modèles** | Entités de données principales | [cite_start]`User`, `Question`, `Test`, `Evaluation` [cite: 176] |
| **Database** | Stockage persistant | [cite_start]MySQL / Base de données relationnelle [cite: 46, 137] |

---

## RÈGLES MÉTIER

Les règles métier (Business Rules - BR) encadrent le fonctionnement logique du système :

1.  [cite_start]**Validation Enseignant** : Un compte enseignant est créé initialement avec des restrictions ; certaines fonctionnalités pédagogiques ne sont accessibles qu'après validation par l'administrateur[cite: 5].
2.  [cite_start]**Unicité des Identifiants** : Chaque utilisateur doit disposer d'une adresse e-mail valide et unique dans le système[cite: 5].
3.  [cite_start]**Gestion des États** : Une question ou un test est enregistré par défaut à l'état "brouillon" et doit être explicitement "publié" pour être visible par les étudiants[cite: 6, 7].
4.  [cite_start]**Intégrité de la Notation** : La note attribuée à une réponse ne peut jamais dépasser le score maximum défini lors de la création de la question[cite: 37, 40].
5.  [cite_start]**Sécurité des Mots de Passe** : Lors de l'inscription, le système vérifie que le mot de passe et sa confirmation correspondent parfaitement[cite: 5, 98].
6.  [cite_start]**Clôture des Tests** : Il est impossible de modifier une évaluation ou d'ajouter un feedback si le test associé est déjà clôturé ou verrouillé[cite: 23, 41].

---

## TECHNOLOGIES ET BIBLIOTHÈQUES

- [cite_start]**Langage** : Java [cite: 176]
- [cite_start]**Interface Graphique** : JavaFX / FXML / CSS [cite: 171, 176]
- [cite_start]**Persistance des Données** : JDBC / MySQL [cite: 55, 137]
- [cite_start]**Modélisation UML** : Cas d'utilisation, activité, séquence et paquets [cite: 3, 43, 44, 47]
- **Gestion de Version** : GitHub

---

## ORGANISATION DU PROJET

```text
Outil-Edition-Questions-Ouvertes/
│
├── README.md         # Documentation principale
├── LICENSE           # Licence du projet
│
├── images/           # Captures d'écran des diagrammes UML (Cas d'utilisation, Séquence, etc.)
│
├── src/
│   ├── view/         # Fichiers d'interface graphique (FXML, CSS)
│   ├── controller/   # Logique des contrôleurs
│   ├── service/      # Logique métier et validation
│   ├── model/        # Classes entités (User, Question, Test)
│   └── dao/          # Objets d'accès aux données (SQL)
│
└── docs/             # Rapports de projet et documentation complémentaire
