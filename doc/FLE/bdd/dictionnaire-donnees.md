# Dictionnaire de données - Plateforme FLE

Ce document décrit les tables et les champs de la base de données pour la plateforme de gestion du Français Langue Étrangère (FLE) de l'association A.I.R.

## Tables de référence

### Roles
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| role_uuid | uuid | Identifiant unique du rôle | Clé primaire |
| rolename | VARCHAR(50) | Nom du rôle | |

### Nationalities
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| nationality_id | INT | Identifiant de la nationalité | Clé primaire |
| label | VARCHAR(256) | Libellé de la nationalité | |

### French_Levels
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| french_level_id | INT | Identifiant du niveau de français | Clé primaire |
| code | VARCHAR(50) | Code du niveau (A1, A2, B1, B2, C1, C2) | |
| description | VARCHAR(50) | Description du niveau | |

### Gender
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| gender_id | INT | Identifiant du genre | Clé primaire |
| label | VARCHAR(50) | Libellé du genre | |

### Addresses
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| address_uuid | uuid | Identifiant unique de l'adresse | Clé primaire |
| street | VARCHAR(50) | Rue | |
| compladress | VARCHAR(50) | Complément d'adresse | |
| zipcode | INT | Code postal | |
| city | VARCHAR(50) | Ville | |
| qpv | VARCHAR(50) | Quartier Prioritaire de la Ville | |

### Exit_Reasons
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| exit_reason_id | VARCHAR(50) | Identifiant de la raison de sortie | Clé primaire |
| reason | VARCHAR(50) | Motif de sortie | |

### Orientations
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| orientation_id | VARCHAR(50) | Identifiant de l'orientation | Clé primaire |
| type | VARCHAR(50) | Type d'orientation | |
| description | VARCHAR(50) | Description de l'orientation | |

### Periods
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| period_id | INT | Identifiant de la période | Clé primaire |
| label | VARCHAR(50) | Libellé de la période | |
| started_at | DATE | Date de début | |
| ended_at | DATE | Date de fin | |
| actual_period | LOGICAL | Période en cours (oui/non) | |

### Sessions
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| session_id | INT | Identifiant de la session | Clé primaire |
| label | VARCHAR(50) | Libellé de la session | |
| started_at | DATE | Date de début | |
| finished_at | DATE | Date de fin | |

### Workings_Hours
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| working_hour_id | VARCHAR(50) | Identifiant des heures de travail | Clé primaire |

### Statuts
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| statut_id | INT | Identifiant du statut | Clé primaire |
| label | VARCHAR(50) | Libellé du statut | |

### Financement
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| financement_id | INT | Identifiant du financement | Clé primaire |
| type | VARCHAR(50) | Type de financement | |

## Tables principales

### Users
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| user_uuid | uuid | Identifiant unique de l'utilisateur | Clé primaire |
| firstname | VARCHAR(50) | Prénom | |
| lastname | VARCHAR(50) | Nom | |
| mail | VARCHAR(50) | Email | NOT NULL, UNIQUE |
| birthdate | DATETIME | Date de naissance | |
| password | VARCHAR(50) | Mot de passe | |
| role_uuid | uuid | Identifiant du rôle | NOT NULL, Clé étrangère → Roles(role_uuid) |

### Students
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| student_uuid | uuid | Identifiant unique de l'apprenant | Clé primaire |
| firstname | VARCHAR(50) | Prénom | |
| lastname | VARCHAR(50) | Nom | |
| birthdate | DATETIME | Date de naissance | |
| placeOfBirth | VARCHAR(50) | Lieu de naissance | |
| mail | VARCHAR(50) | Email | |
| phone | VARCHAR(50) | Téléphone | |
| date_test_initial | VARCHAR(50) | Date du test initial | |
| commentaire | VARCHAR(50) | Commentaires | |
| date_entree_france | VARCHAR(50) | Date d'entrée en France | |
| financement_id | INT | Identifiant du financement | NOT NULL, Clé étrangère → Financement(financement_id) |
| statut_id | INT | Identifiant du statut | NOT NULL, Clé étrangère → Statuts(statut_id) |
| orientation_id | VARCHAR(50) | Identifiant de l'orientation | NOT NULL, Clé étrangère → Orientations(orientation_id) |
| exit_reason_id | VARCHAR(50) | Identifiant de la raison de sortie | NOT NULL, Clé étrangère → Exit_Reasons(exit_reason_id) |
| french_level_id | INT | Niveau de français initial | NOT NULL, Clé étrangère → French_Levels(french_level_id) |
| french_level_id_1 | INT | Niveau de français final | NOT NULL, Clé étrangère → French_Levels(french_level_id) |
| nationality_id | INT | Identifiant de la nationalité | NOT NULL, Clé étrangère → Nationalities(nationality_id) |
| gender_id | INT | Identifiant du genre | NOT NULL, Clé étrangère → Gender(gender_id) |

### Todolists
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| todo_list_uuid | uuid | Identifiant unique de la liste de tâches | Clé primaire |
| title | VARCHAR(50) | Titre | |
| description | VARCHAR(50) | Description | |
| createdAt | DATETIME | Date de création | |
| updatedAt | DATETIME | Date de mise à jour | |
| dueAt | DATETIME | Date d'échéance | |
| completionpercentage | DECIMAL(15,2) | Pourcentage d'achèvement | |
| user_uuid | uuid | Identifiant de l'utilisateur | NOT NULL, Clé étrangère → Users(user_uuid) |

### Groups
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| group_id | INT | Identifiant du groupe | Clé primaire |
| label | VARCHAR(50) | Libellé du groupe | |
| session_id | INT | Identifiant de la session | NOT NULL, Clé étrangère → Sessions(session_id) |

### Courses
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| session_id | INT | Identifiant de la session | Clé primaire |
| day_ | DATE | Jour | |
| start_hour | DATE | Heure de début | |
| end_hour | DATE | Heure de fin | |
| intitule | VARCHAR(50) | Intitulé du cours | |
| group_id | INT | Identifiant du groupe | NOT NULL, Clé étrangère → Groups(group_id) |

### Examens
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| examen_id | INT | Identifiant de l'examen | Clé primaire |
| label | VARCHAR(50) | Libellé de l'examen | |
| taked_at | DATE | Date de passage | |
| note | VARCHAR(50) | Note obtenue | |
| student_uuid | uuid | Identifiant de l'apprenant | NOT NULL, Clé étrangère → Students(student_uuid) |

### Continuation
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| continuation_id | INT | Identifiant du suivi | Clé primaire |
| temporalite | VARCHAR(50) | Temporalité (6 mois, 12 mois) | |
| commentary | VARCHAR(50) | Commentaire de suivi | |
| student_uuid | uuid | Identifiant de l'apprenant | NOT NULL, Clé étrangère → Students(student_uuid) |

### Absences
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| absence_id | INT | Identifiant de l'absence | Clé primaire |
| reason | VARCHAR(50) | Motif de l'absence | |
| student_uuid | uuid | Identifiant de l'apprenant | NOT NULL, Clé étrangère → Students(student_uuid) |
| session_id | INT | Identifiant de la session | NOT NULL, Clé étrangère → Courses(session_id) |

## Tables de relation

### Resides_At
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → Students(student_uuid) |
| address_uuid | uuid | Identifiant de l'adresse | Clé primaire, Clé étrangère → Addresses(address_uuid) |

### Belong
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| student_uuid | uuid | Identifiant de l'apprenant | Clé primaire, Clé étrangère → Students(student_uuid) |
| group_id | INT | Identifiant du groupe | Clé primaire, Clé étrangère → Groups(group_id) |

### Dispense
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| user_uuid | uuid | Identifiant de l'utilisateur | Clé primaire, Clé étrangère → Users(user_uuid) |
| session_id | INT | Identifiant de la session | Clé primaire, Clé étrangère → Courses(session_id) |

### Concern
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| period_id | INT | Identifiant de la période | Clé primaire, Clé étrangère → Periods(period_id) |
| group_id | INT | Identifiant du groupe | Clé primaire, Clé étrangère → Groups(group_id) |

### Work
| Champ | Type | Description | Contrainte |
|-------|------|-------------|------------|
| user_uuid | uuid | Identifiant de l'utilisateur | Clé primaire, Clé étrangère → Users(user_uuid) |
| working_hour_id | VARCHAR(50) | Identifiant des heures de travail | Clé primaire, Clé étrangère → Workings_Hours(working_hour_id) |
