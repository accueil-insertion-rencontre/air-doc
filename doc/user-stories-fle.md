# User Stories - Plateforme FLE

## Définition
Les user stories sont un moyen d'exprimer les fonctionnalités du point de vue de l'utilisateur. Elles suivent le format "En tant que [rôle], je souhaite [action] afin de [bénéfice]". Les user stories sont numérotées pour faciliter le référencement.

## Nomenclature
- **US-ADM-XXX** : User stories pour les administrateurs
- **US-FOR-XXX** : User stories pour les formateurs

## Administrateur

### Gestion des utilisateurs
**US-ADM-001** : En tant qu'administrateur, je souhaite pouvoir créer des comptes utilisateurs pour les formateurs afin qu'ils puissent accéder à la plateforme FLE.

**US-ADM-002** : En tant qu'administrateur, je souhaite pouvoir définir les rôles et permissions des utilisateurs afin de contrôler l'accès aux différentes fonctionnalités.

**US-ADM-003** : En tant qu'administrateur, je souhaite pouvoir désactiver des comptes utilisateurs afin de gérer les départs des formateurs.

### Accès à la plateforme
**US-ADM-004** : En tant qu'administrateur, je souhaite pouvoir me connecter à la plateforme FLE afin d'accéder à mes fonctionnalités spécifiques.

### Suivi et statistiques
**US-ADM-005** : En tant qu'administrateur, je souhaite pouvoir consulter les statistiques globales des formations afin d'avoir une vue d'ensemble des activités FLE.

**US-ADM-006** : En tant qu'administrateur, je souhaite pouvoir consulter les heures de travail des formateurs afin de suivre leur activité.

**US-ADM-007** : En tant qu'administrateur, je souhaite pouvoir générer des rapports sur l'évolution des niveaux de français des étudiants afin d'évaluer l'efficacité globale des formations.

## Formateur

### Accès à la plateforme
**US-FOR-001** : En tant que formateur, je souhaite pouvoir me connecter à la plateforme FLE afin d'accéder à mes fonctionnalités spécifiques.

### Gestion des étudiants

#### Informations personnelles
**US-FOR-002** : En tant que formateur, je souhaite pouvoir enregistrer un nouvel étudiant avec ses informations personnelles (nom, prénom, date de naissance, téléphone, sexe, lieu de naissance) afin de commencer son suivi.

**US-FOR-003** : En tant que formateur, je souhaite pouvoir modifier les informations personnelles d'un étudiant afin de maintenir ses données à jour.

#### Informations complémentaires
**US-FOR-004** : En tant que formateur, je souhaite pouvoir associer une nationalité à un étudiant afin de compléter son profil.

**US-FOR-005** : En tant que formateur, je souhaite pouvoir associer une adresse complète (rue, complément, code postal, ville) à un étudiant afin de faciliter le suivi et la communication.

**US-FOR-006** : En tant que formateur, je souhaite pouvoir indiquer si l'étudiant réside en QPV (Quartier Prioritaire de la Ville) afin de suivre les indicateurs sociaux.

#### Niveau de français et statut
**US-FOR-007** : En tant que formateur, je souhaite pouvoir enregistrer et mettre à jour le niveau de français initial d'un étudiant afin d'adapter la formation à ses besoins.

**US-FOR-008** : En tant que formateur, je souhaite pouvoir enregistrer et mettre à jour le niveau de français final d'un étudiant afin de mesurer sa progression.

**US-FOR-009** : En tant que formateur, je souhaite pouvoir enregistrer le statut administratif d'un étudiant avec son code et sa description afin de suivre sa situation.

#### Recherche et consultation
**US-FOR-010** : En tant que formateur, je souhaite pouvoir effectuer des recherches multicritères sur les étudiants afin de trouver rapidement les informations dont j'ai besoin.

**US-FOR-011** : En tant que formateur, je souhaite pouvoir consulter la liste complète de tous les étudiants afin d'avoir une vue d'ensemble.

**US-FOR-012** : En tant que formateur, je souhaite pouvoir consulter le profil détaillé d'un étudiant afin d'accéder à l'ensemble de ses informations.

### Gestion des groupes et sessions

#### Création et organisation des groupes
**US-FOR-013** : En tant que formateur, je souhaite pouvoir créer et gérer des groupes d'étudiants afin d'organiser les formations.

**US-FOR-014** : En tant que formateur, je souhaite pouvoir ajouter ou retirer des étudiants d'un groupe afin d'adapter la composition selon les besoins.

#### Sessions de formation
**US-FOR-015** : En tant que formateur, je souhaite pouvoir créer et gérer des sessions de formation avec dates de début et fin afin de planifier le calendrier de formation.

**US-FOR-016** : En tant que formateur, je souhaite pouvoir associer des groupes à des sessions de formation afin de définir qui participe à quelle formation.

**US-FOR-017** : En tant que formateur, je souhaite pouvoir définir des périodes spécifiques dans les sessions afin de structurer le parcours pédagogique.

### Gestion des cours

#### Planification des cours
**US-FOR-018** : En tant que formateur, je souhaite pouvoir créer et planifier des cours avec horaires précis (heure de début et fin) afin d'organiser l'emploi du temps.

**US-FOR-019** : En tant que formateur, je souhaite pouvoir associer des cours à des sessions de formation afin de structurer le programme.

#### Types de cours spécifiques
**US-FOR-020** : En tant que formateur, je souhaite accéder à des cours d'insertion professionnelle afin de les inclure dans mon programme de formation.

**US-FOR-021** : En tant que formateur, je souhaite accéder à des cours dédiés au code de la route afin de les inclure dans mon programme de formation.

### Suivi des présences et absences

#### Gestion des absences
**US-FOR-022** : En tant que formateur, je souhaite pouvoir enregistrer les absences des étudiants aux cours afin de suivre leur assiduité.

**US-FOR-023** : En tant que formateur, je souhaite pouvoir indiquer le motif d'une absence afin de différencier les absences justifiées des non-justifiées.

#### Consultation des présences
**US-FOR-024** : En tant que formateur, je souhaite pouvoir consulter l'historique des absences d'un étudiant afin d'évaluer sa participation globale.

**US-FOR-025** : En tant que formateur, je souhaite recevoir une notification après plusieurs absences répétées d'un étudiant afin de pouvoir intervenir rapidement.

### Parcours et orientation

#### Parcours professionnel
**US-FOR-026** : En tant que formateur, je souhaite pouvoir enregistrer les périodes de travail des étudiants (dates de début, fin et statut) afin de suivre leur insertion professionnelle.

#### Orientation et suivi de parcours
**US-FOR-027** : En tant que formateur, je souhaite pouvoir enregistrer les orientations des étudiants avec leur description afin de suivre leur parcours d'insertion.

**US-FOR-028** : En tant que formateur, je souhaite pouvoir enregistrer les raisons de sortie des étudiants afin de documenter leur départ.

**US-FOR-029** : En tant que formateur, je souhaite pouvoir enregistrer des informations de financement pour chaque étudiant afin de suivre leurs droits.

**US-FOR-030** : En tant que formateur, je souhaite pouvoir enregistrer des informations sur la continuation du parcours d'un étudiant (opportunité, bénéficiaire) afin de suivre son évolution post-formation.

### Examens et évaluations

#### Gestion des examens
**US-FOR-031** : En tant que formateur, je souhaite pouvoir enregistrer les examens avec leurs descriptions et résultats afin d'évaluer les étudiants.

**US-FOR-032** : En tant que formateur, je souhaite pouvoir associer des examens aux groupes d'étudiants afin d'organiser les évaluations.

**US-FOR-033** : En tant que formateur, je souhaite pouvoir consulter les résultats d'examens par étudiant afin de suivre leurs progrès individuels.

### Gestion des ressources et documents

#### Partage de documents
**US-FOR-034** : En tant que formateur, je souhaite pouvoir partager des documents avec les étudiants afin de leur fournir du matériel pédagogique.

**US-FOR-035** : En tant que formateur, je souhaite pouvoir organiser les documents par thématique ou par niveau afin de faciliter leur accès.

#### Suivi du temps de travail
**US-FOR-036** : En tant que formateur, je souhaite pouvoir enregistrer mes heures de travail afin de suivre mon activité professionnelle.

**US-FOR-037** : En tant que formateur, je souhaite pouvoir consulter un récapitulatif de mes heures de travail sur une période donnée afin de faire le bilan de mon activité.

### Rapports et attestations

#### Génération de statistiques
**US-FOR-038** : En tant que formateur, je souhaite pouvoir générer des rapports statistiques sur la progression des étudiants afin d'évaluer l'efficacité de la formation.

**US-FOR-039** : En tant que formateur, je souhaite pouvoir filtrer les statistiques par groupe ou par période afin d'analyser des segments spécifiques.

#### Documents officiels
**US-FOR-040** : En tant que formateur, je souhaite pouvoir générer des attestations de présence pour les étudiants afin de valider leur participation.

**US-FOR-041** : En tant que formateur, je souhaite pouvoir générer des attestations de niveau pour les étudiants afin de certifier leurs compétences acquises.

### Gestion des tâches

**US-FOR-042** : En tant que formateur, je souhaite pouvoir créer et gérer des tâches avec description, pourcentage de complétion et date d'échéance afin d'organiser mon travail.

**US-FOR-043** : En tant que formateur, je souhaite pouvoir marquer une tâche comme terminée afin de suivre ma progression.

**US-FOR-044** : En tant que formateur, je souhaite pouvoir prioriser mes tâches afin de me concentrer sur les actions les plus importantes. 