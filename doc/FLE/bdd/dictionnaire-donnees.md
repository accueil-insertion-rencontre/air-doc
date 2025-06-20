# Dictionnaire de données - Plateforme FLE

Ce document décrit les tables et les champs de la base de données pour la plateforme de gestion du Français Langue Étrangère (FLE) de l'association A.I.R., conformément au schéma SQL fourni.

## Tables de référence

### Roles
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| role_uuid | uuid | Identifiant unique du rôle | Clé primaire | `'a1b2c3d4-e5f6-7890-1234-567890abcdef'` |
| role_name | VARCHAR(50) | Nom du rôle (ex: "Admin", "Formateur") | | `'Formateur'` |

### Nationalities
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| nationality_uuid | uuid | Identifiant unique de la nationalité | Clé primaire | `'b1c2d3e4-f5a6-b789-c123-d4567890123e'` |
| nationality_label | VARCHAR(256) | Libellé de la nationalité | | `'Afghane'` |

### French_Levels
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| french_level_uuid | uuid | Identifiant unique du niveau de français | Clé primaire | `'c1d2e3f4-a5b6-c789-d123-e4567890123f'` |
| french_level_code | VARCHAR(50) | Code du niveau (A1, A2, B1...) | | `'A2'` |
| french_level_description | VARCHAR(50) | Description du niveau | | `'Niveau élémentaire'` |

### Genders
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| gender_uuid | uuid | Identifiant unique du genre | Clé primaire | `'d1e2f3a4-b5c6-d789-e123-f4567890123a'` |
| gender_label | VARCHAR(50) | Libellé du genre | | `'Femme'` |

### Exit_Reasons
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| exit_reason_uuid | uuid | Identifiant unique de la raison de sortie | Clé primaire | `'e1f2a3b4-c5d6-e789-f123-a4567890123b'` |
| exit_reason | VARCHAR(50) | Motif de la sortie de la formation | | `'Obtention d'un emploi'` |

### Orientations
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| orientation_uuid | uuid | Identifiant unique de l'orientation post-formation | Clé primaire | `'f1a2b3c4-d5e6-f789-a123-b4567890123c'` |
| orientation_type | VARCHAR(50) | Type d'orientation (ex: "Emploi", "Formation qualifiante") | | `'Formation qualifiante'` |
| orientation_description | VARCHAR(50) | Description de l'orientation | | `'Formation en cuisine'` |

### Periods
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| period_uuid | uuid | Identifiant unique de la période | Clé primaire | `'a2b3c4d5-e6f7-a890-1234-567890abcdef'` |
| period_label | VARCHAR(50) | Libellé de la période (ex: "Session 1 - 2024") | | `'Année 2024-2025'` |
| period_started_at | DATE | Date de début de la période | | `'2024-09-01'` |
| period_ended_at | DATE | Date de fin de la période | | `'2025-06-30'` |
| period_actual_period | LOGICAL | Indique si c'est la période en cours | | `true` |

### Sessions
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| session_uuid | uuid | Identifiant unique de la session de cours | Clé primaire | `'b2c3d4e5-f6a7-b890-c123-d4567890123e'` |
| session_label | VARCHAR(50) | Libellé de la session | | `'Session 1'` |
| session_started_at | DATE | Date de début de la session | | `'2024-09-01'` |
| session_finished_at | DATE | Date de fin de la session | | `'2024-11-15'` |

### Status
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| status_uuid | uuid | Identifiant unique du statut de l'apprenant | Clé primaire | `'c2d3e4f5-a6b7-c890-d123-e4567890123f'` |
| status_label | VARCHAR(50) | Libellé du statut (ex: "Demandeur d'asile", "BPI") | | `'Demandeur d''asile'` |

### financings
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| financing_uuid | uuid | Identifiant unique du type de financement | Clé primaire | `'d2e3f4a5-b6c7-d890-e123-f4567890123a'` |
| financing_type | VARCHAR(50) | Type de financement (ex: "OFII", "Personnel") | | `'OFII'` |

## Tables principales

### Users
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| user_uuid | uuid | Identifiant unique de l'utilisateur | Clé primaire | `'a1b2c3d4-e5f6-7890-1234-567890abcdef'` |
| user_firstname | VARCHAR(50) | Prénom de l'utilisateur | | `'Nathalie'` |
| user_lastname | VARCHAR(50) | Nom de l'utilisateur | | `'Dupont'` |
| user_mail | VARCHAR(50) | Email de l'utilisateur | NOT NULL, UNIQUE | `'nathalie.dupont@air.fr'` |
| user_birthdate | DATETIME | Date de naissance de l'utilisateur | | `'1985-02-10 00:00:00'` |
| user_password | VARCHAR(50) | Mot de passe (haché) | | `'hashed_password_string'` |
| role_uuid | uuid | Rôle de l'utilisateur | NOT NULL, Clé étrangère → Roles(role_uuid) | `'a1b2c3d4-e5f6-7890-1234-567890abcdef'` |

### students
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| student_uuid | uuid | Identifiant unique de l'apprenant | Clé primaire | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| student_firstname | VARCHAR(50) | Prénom de l'apprenant | | `'Fatima'` |
| student_lastname | VARCHAR(50) | Nom de l'apprenant | | `'Al-Sayed'` |
| student_birthdate | DATETIME | Date de naissance | | `'1998-07-20 00:00:00'` |
| student_place_of_birth | VARCHAR(50) | Lieu de naissance | | `'Damas'` |
| student_mail | VARCHAR(50) | Email de l'apprenant | | `'fatima.alsayed@email.com'` |
| student_phone | VARCHAR(50) | Téléphone de l'apprenant | | `'0612345678'` |
| student_date_test_initial | DATE | Date du test de positionnement initial | | `'2024-09-05'` |
| student_commentary | VARCHAR(50) | Commentaire général sur l'apprenant | | `'Très motivée'` |
| student_date_entree_france | DATETIME | Date d'entrée en France | | `'2023-05-15 00:00:00'` |
| financing_uuid | uuid | Financement de la formation | NOT NULL, Clé étrangère → financings(financing_uuid) | `'d2e3f4a5-b6c7-d890-e123-f4567890123a'` |
| status_uuid | uuid | Statut de l'apprenant | NOT NULL, Clé étrangère → Status(status_uuid) | `'c2d3e4f5-a6b7-c890-d123-e4567890123f'` |
| orientation_uuid | uuid | Orientation à la sortie | NOT NULL, Clé étrangère → Orientations(orientation_uuid) | `'f1a2b3c4-d5e6-f789-a123-b4567890123c'` |
| exit_reason_uuid | uuid | Motif de la sortie | NOT NULL, Clé étrangère → Exit_Reasons(exit_reason_uuid) | `'e1f2a3b4-c5d6-e789-f123-a4567890123b'` |
| french_level_uuid | uuid | Niveau de français initial (à l'entrée) | NOT NULL, Clé étrangère → French_Levels(french_level_uuid) | `'c1d2e3f4-a5b6-c789-d123-e4567890123f'` |
| gender_uuid | uuid | Genre de l'apprenant | NOT NULL, Clé étrangère → Genders(gender_uuid) | `'d1e2f3a4-b5c6-d789-e123-f4567890123a'` |

### Addresses
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| address_uuid | uuid | Identifiant unique de l'adresse | Clé primaire | `'f2a3b4c5-d6e7-f890-a123-b4567890123c'` |
| adress_street | VARCHAR(50) | Rue | | `'10 Rue Nationale'` |
| adress_compladress | VARCHAR(50) | Complément d'adresse | | `'Appartement 5'` |
| adress_zipcode | INT | Code postal | | `59200` |
| adress_city | VARCHAR(50) | Ville | | `'Tourcoing'` |

### Tasks
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| task_uuid | uuid | Identifiant unique de la tâche | Clé primaire | `'a3b4c5d6-e7f8-a901-b234-c567890def12'` |
| task_title | VARCHAR(50) | Titre de la tâche | | `'Préparer évaluation A1'` |
| task_description | VARCHAR(50) | Description de la tâche | | `'Créer le sujet et les fiches de notes'` |
| task_status | DECIMAL(15,2) | État d'avancement (ex: pourcentage) | | `50.00` |
| task_created_at | DATETIME | Date de création | | `'2024-10-01 10:00:00'` |
| task_updated_at | DATETIME | Date de dernière modification | | `'2024-10-02 15:30:00'` |
| task_due_at | DATETIME | Date d'échéance | | `'2024-10-10 18:00:00'` |
| user_uuid | uuid | Utilisateur assigné à la tâche | Clé étrangère → Users(user_uuid) | `'a1b2c3d4-e5f6-7890-1234-567890abcdef'` |

### Subtasks
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| subtask_uuid | uuid | Identifiant unique de la sous-tâche | Clé primaire | `'b3c4d5e6-f7a8-b901-c234-d567890ef123'` |
| subtask_title | VARCHAR(50) | Titre de la sous-tâche | | `'Imprimer les sujets'` |
| subtask_description | VARCHAR(50) | Description de la sous-tâche | | `'30 copies'` |
| subtask_status | VARCHAR(50) | Statut de la sous-tâche | | `'Terminé'` |
| subtask_created_at | DATETIME | Date de création | | `'2024-10-03 09:00:00'` |
| subtask_updated_at | DATETIME | Date de dernière modification | | `'2024-10-03 11:00:00'` |
| task_uuid | uuid | Tâche parente | NOT NULL, Clé étrangère → Tasks(task_uuid) | `'a3b4c5d6-e7f8-a901-b234-c567890def12'` |

### Groups
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| group_uuid | uuid | Identifiant unique du groupe d'apprenants | Clé primaire | `'c3d4e5f6-a7b8-c901-d234-e567890f1234'` |
| group_label | VARCHAR(50) | Nom du groupe (ex: "A1 Matin") | | `'A1 Matin - Lundi/Mardi'` |
| session_uuid | uuid | Session à laquelle le groupe appartient | NOT NULL, Clé étrangère → Sessions(session_uuid) | `'b2c3d4e5-f6a7-b890-c123-d4567890123e'` |

### Courses
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| course_uuid | uuid | Identifiant unique du cours | Clé primaire | `'d3e4f5a6-b7c8-d901-e234-f567890a1234'` |
| course_name | VARCHAR(50) | Intitulé du cours | | `'Grammaire'` |
| course_day | DATE | Jour du cours | | `'2024-09-09'` |
| course_start_hour | DATETIME | Heure de début | | `'2024-09-09 09:00:00'` |
| course_end_hour | DATETIME | Heure de fin | | `'2024-09-09 11:00:00'` |
| group_uuid | uuid | Groupe qui suit le cours | NOT NULL, Clé étrangère → Groups(group_uuid) | `'c3d4e5f6-a7b8-c901-d234-e567890f1234'` |

### Exams
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| exam_uuid | uuid | Identifiant unique de l'examen | Clé primaire | `'e3f4a5b6-c7d8-e901-f234-a567890b1234'` |
| exam_label | VARCHAR(50) | Libellé de l'examen | | `'Examen final A1'` |
| exam_taked_at | DATE | Date de passage | | `'2024-11-10'` |
| exam_score | VARCHAR(50) | Note/Score obtenu | | `'85/100'` |
| student_uuid | uuid | Apprenant qui a passé l'examen | NOT NULL, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |

### Continuations
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| continuation_uuid | uuid | Identifiant unique du suivi post-formation | Clé primaire | `'f3a4b5c6-d7e8-f901-a234-b567890c1234'` |
| continuation_temporality | DATETIME | Date du point de suivi (ex: à 6 mois) | | `'2025-05-10 00:00:00'` |
| continuation_commentary | VARCHAR(50) | Commentaire sur la situation de l'apprenant | | `'A trouvé un CDD'` |
| student_uuid | uuid | Apprenant concerné par le suivi | NOT NULL, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |

### Absences
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| absence_uuid | uuid | Identifiant unique de l'absence | Clé primaire | `'a4b5c6d7-e8f9-a012-b345-c67890d12345'` |
| absence_reason | VARCHAR(50) | Motif de l'absence | | `'Rendez-vous médical'` |
| student_uuid | uuid | Apprenant absent | NOT NULL, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| course_uuid | uuid | Cours manqué | NOT NULL, Clé étrangère → Courses(course_uuid) | `'d3e4f5a6-b7c8-d901-e234-f567890a1234'` |

## Tables de relation

### Declare_
*Relation (N,N) entre les apprenants et leurs nationalités.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| nationality_uuid | uuid | Identifiant de la nationalité | Clé primaire, Clé étrangère → Nationalities(nationality_uuid) | `'b1c2d3e4-f5a6-b789-c123-d4567890123e'` |

### Exit
*Relation (N,N) pour stocker le niveau de français final d'un apprenant à sa sortie.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| french_level_uuid | uuid | Identifiant du niveau de français | Clé primaire, Clé étrangère → French_Levels(french_level_uuid) | `'c1d2e3f4-a5b6-c789-d123-e4567890123f'` |

### Reside
*Relation (N,N) entre les apprenants et leurs adresses.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| address_uuid | uuid | Identifiant de l'adresse | Clé primaire, Clé étrangère → Addresses(address_uuid) | `'f2a3b4c5-d6e7-f890-a123-b4567890123c'` |

### Join_
*Relation (N,N) entre les apprenants et les groupes.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → students(student_uuid) | `'e2f3a4b5-c6d7-e890-f123-a4567890123b'` |
| group_uuid | uuid | Identifiant du groupe | Clé primaire, Clé étrangère → Groups(group_uuid) | `'c3d4e5f6-a7b8-c901-d234-e567890f1234'` |

### Teach
*Relation (N,N) entre les formateurs (utilisateurs) et les cours qu'ils dispensent.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| user_uuid | uuid | Identifiant de l'utilisateur (formateur) | Clé primaire, Clé étrangère → Users(user_uuid) | `'a1b2c3d4-e5f6-7890-1234-567890abcdef'` |
| course_uuid | uuid | Identifiant du cours | Clé primaire, Clé étrangère → Courses(course_uuid) | `'d3e4f5a6-b7c8-d901-e234-f567890a1234'` |

### Cover
*Relation (N,N) entre les périodes et les groupes.*
| Champ | Type | Description | Contrainte | Exemple |
|---|---|---|---|---|
| period_uuid | uuid | Identifiant de la période | Clé primaire, Clé étrangère → Periods(period_uuid) | `'a2b3c4d5-e6f7-a890-1234-567890abcdef'` |
| group_uuid | uuid | Identifiant du groupe | Clé primaire, Clé étrangère → Groups(group_uuid) | `'c3d4e5f6-a7b8-c901-d234-e567890f1234'` |
