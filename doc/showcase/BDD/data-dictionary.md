# Dictionnaire de données – Base AIR

| Table      | Attribut          | Type         | Contraintes                           | Description                             |
|:-----------|:------------------|:-------------|:--------------------------------------|:----------------------------------------|
| Users      | user_id           | UUID         | PK, NOT NULL                          | Clé primaire de l'utilisateur           |
| Users      | firstname         | VARCHAR(50)  | NOT NULL                              | Prénom de l'utilisateur                 |
| Users      | lastname          | VARCHAR(50)  | NOT NULL                              | Nom de l'utilisateur                    |
| Users      | mail              | VARCHAR(255) | UNIQUE, NOT NULL                      | Adresse email de l'utilisateur          |
| Users      | password          | VARCHAR(100) | NOT NULL                              | Mot de passe hashé                      |
| Users      | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Users      | updated_at        | DATETIME     | NOT NULL                              | Date de dernière mise à jour            |
| Partners   | parteners_id      | INTEGER      | PK, NOT NULL                          | Clé primaire du partenaire              |
| Partners   | name              | VARCHAR(100) | NOT NULL                              | Nom du partenaire                       |
| Partners   | image_url         | VARCHAR(500) | NOT NULL                              | Logo du partenaire                      |
| Partners   | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Partners   | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Partners   | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur associé       |
| Times      | time_id           | INTEGER      | PK, NOT NULL                          | Clé primaire de l'événement temporel    |
| Times      | year              | INTEGER      | NOT NULL                              | Année de l'événement                    |
| Times      | event_description | VARCHAR(175) | NOT NULL                              | Description de l'événement              |
| Times      | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Times      | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Times      | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur associé       |
| Job_offers | job_offer_id      | INTEGER      | PK, NOT NULL                          | Clé primaire de l'offre d'emploi        |
| Job_offers | name              | VARCHAR(60)  | NOT NULL                              | Titre de l'offre                        |
| Job_offers | job_type          | VARCHAR(60)  |                                       | Type de contrat                         |
| Job_offers | city              | VARCHAR(50)  |                                       | Ville                                   |
| Job_offers | image_url         | VARCHAR(500) |                                       | Image illustrative                      |
| Job_offers | description       | VARCHAR(350) |                                       | Description de l'offre                  |
| Job_offers | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Job_offers | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Job_offers | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Structures | structure_id      | INTEGER      | PK, NOT NULL                          | Clé primaire de la structure            |
| Structures | name              | VARCHAR(60)  | NOT NULL                              | Nom de la structure                     |
| Structures | image_url         | VARCHAR(500) |                                       | Image ou logo                           |
| Structures | description       | VARCHAR(330) | NOT NULL                              | Description                             |
| Structures | address           | VARCHAR(255) |                                       | Adresse                                 |
| Structures | phone_number      | VARCHAR(25)  |                                       | Numéro de téléphone                     |
| Structures | missions          | VARCHAR(250) |                                       | Missions                                |
| Structures | link              | VARCHAR      |                                       | Lien vers la structure                  |
| Structures | schedule          | VARCHAR(200) |                                       | Horaires                                |
| Structures | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Structures | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Structures | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Statistics | statistic_id      | INTEGER      | PK, NOT NULL                          | Clé primaire de la statistique          |
| Statistics | label             | VARCHAR(100) | NOT NULL                              | Titre de la statistique                 |
| Statistics | value             | INTEGER      | NOT NULL                              | Valeur                                  |
| Statistics | year              | INTEGER      | NOT NULL                              | Année                                   |
| Statistics | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Statistics | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Statistics | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| News       | news_id           | INTEGER      | PK, NOT NULL                          | Clé primaire de l'actualité             |
| News       | name              | VARCHAR(100) | NOT NULL                              | Titre de l'actualité                    |
| News       | image_url         | VARCHAR(500) |                                       | Image                                   |
| News       | description       | VARCHAR(300) |                                       | Description                             |
| News       | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| News       | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| News       | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Values     | value_id          | INTEGER      | PK, NOT NULL                          | Clé primaire de la valeur               |
| Values     | name              | VARCHAR(100) | NOT NULL                              | Nom de la valeur                        |
| Values     | image_url         | VARCHAR(500) |                                       | Image                                   |
| Values     | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Values     | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Values     | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Positions  | position_id       | INTEGER      | PK, NOT NULL                          | Clé primaire du niveau de qualification |
| Positions  | name              | VARCHAR(100) | NOT NULL                              | Nom du niveau de qualification          |
| Positions  | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Positions  | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Jobs       | job_id            | INTEGER      | PK, NOT NULL                          | Clé primaire du poste                   |
| Jobs       | function          | VARCHAR(100) | NOT NULL                              | Intitulé de la fonction                 |
| Jobs       | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Jobs       | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Jobs       | position_id       | INTEGER      | FK → Positions(position_id), NOT NULL | Référence au niveau de qualification    |
| Jobs       | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Steps      | step_id           | INTEGER      | PK, NOT NULL                          | Clé primaire de l'étape                 |
| Steps      | name              | VARCHAR(100) | NOT NULL                              | Nom de l'étape                          |
| Steps      | image_url         | VARCHAR(500) |                                       | Image de l'étape                        |
| Steps      | description       | VARCHAR(390) |                                       | Description                             |
| Steps      | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Steps      | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |
| Steps      | user_id           | UUID         | FK → Users(user_id), NOT NULL         | Référence à l'utilisateur               |
| Steps      | path_id           | INTEGER      | FK → Paths(path_id), NOT NULL         | Référence au parcours                   |
| Paths      | path_id           | INTEGER      | PK, NOT NULL                          | Clé primaire du parcours                |
| Paths      | name              | VARCHAR(20)  | NOT NULL, UNIQUE                      | Nom du parcours                         |
| Paths      | created_at        | DATETIME     | NOT NULL                              | Date de création                        |
| Paths      | updated_at        | DATETIME     | NOT NULL                              | Date de mise à jour                     |