
# EVENTPRT — Plateforme de gestion d’événements

**Module :** Cloud Computing (B3COM0204)  
**Organisation :** Groupe de 6 membres  
**Année académique :** 2026-2027

---

## 1. Présentation du projet

EventPRT est une plateforme web de gestion d'événements permettant aux utilisateurs de créer un compte, de consulter les événements disponibles, de voir les détails d'un événement et d'effectuer des réservations de places.

Le projet repose sur les services Cloud d'Amazon Web Services (AWS).

### Objectifs du projet

- Faciliter la consultation des événements.
- Permettre aux utilisateurs de créer un compte et de se connecter.
- Permettre la création et la gestion des événements.
- Gérer les réservations et leur annulation.
- Héberger l'application sur une infrastructure Cloud.
- Assurer la sécurité des données et la maîtrise des coûts.

## 2. Fonctionnalités de l'application

### Interface utilisateur (Frontend)

- Page d'accueil.
- Catalogue des événements.
- Page de détails d'un événement.
- Tableau de bord.
- Page de contact.
- Formulaire d'inscription et de connexion.
- Formulaire de création d'événement avec validation.
- Formulaire de contact.
- Design responsive (mobile, tablette et ordinateur).

### Traitement côté serveur (Backend)

Les fonctions AWS Lambda assurent :

- L'inscription des utilisateurs (register).
- La connexion des utilisateurs (login).
- La création d'événements (create).
- La liste des événements (list).
- La consultation d'un événement par son identifiant (getById).
- La création des réservations (create).
- La consultation des réservations (list).
- L'annulation des réservations (cancel).

## 3. Architecture Cloud du projet

Le projet utilise plusieurs services AWS qui travaillent ensemble.

### Services utilisés

| Service AWS | Rôle |
|---|---|
| Amazon S3 | Hébergement du frontend |
| Amazon CloudFront | Distribution du site et activation HTTPS |
| Amazon API Gateway | Gestion des requêtes API |
| AWS Lambda | Traitement des opérations côté serveur |
| Amazon DynamoDB | Stockage des données |
| Amazon CloudWatch | Surveillance et gestion des logs |
| AWS IAM | Gestion des rôles et permissions |
| AWS Budgets | Surveillance des coûts |

### Fonctionnement de l'architecture

1. L'utilisateur accède au site web.
2. Le frontend est hébergé sur Amazon S3.
3. CloudFront assure la distribution du contenu et l'accès HTTPS lorsqu'il est configuré.
4. Les requêtes destinées au backend passent par API Gateway.
5. AWS Lambda exécute les opérations demandées.
6. DynamoDB stocke les informations des utilisateurs, événements et réservations.
7. CloudWatch permet de surveiller les erreurs et les journaux d'exécution.
8. IAM contrôle les autorisations des différents services.

## 4. Technologies utilisées

- React : développement de l'interface utilisateur.
- React Router : navigation entre les pages.
- AWS Lambda : traitement côté serveur.
- Amazon DynamoDB : base de données NoSQL.
- Amazon S3 : stockage et hébergement.
- Amazon API Gateway : création des API.
- Amazon CloudFront : distribution du contenu.
- Amazon CloudWatch : surveillance.
- AWS IAM : sécurité et gestion des accès.
- Git et GitHub : gestion du code source.

## 5. Organisation du projet

L'organisation prévue du dépôt est la suivante :

```text
EventPRT/
│
├── eventflow-frontend/
│   └── src/
│       ├── pages/
│       └── components/
│
├── aws-serverless/
│   └── lambda/
│
├── README.md
└── .gitignore
```

- `eventflow-frontend/src/pages/` : contient les différentes pages.
- `eventflow-frontend/src/components/` : contient les composants réutilisables.
- `aws-serverless/lambda/` : contient les fonctions AWS Lambda.
- `README.md` : documentation du projet.
- `.gitignore` : permet d'exclure les fichiers sensibles du dépôt.

## 6. Installation et exécution en local

### Prérequis

- Node.js.
- npm.
- Git.
- Un compte AWS.
- Un accès au dépôt GitHub du projet.

### Récupération du projet

```bash
git clone <URL_DU_DEPOT>
cd <NOM_DU_DEPOT>
```

### Installation du frontend

```bash
cd eventflow-frontend
npm install
```

### Lancement de l'application

```bash
npm run dev
```

La commande de démarrage doit correspondre aux scripts définis dans le fichier package.json.

## 7. Procédure de déploiement AWS

Le déploiement de l'application s'effectue en plusieurs étapes.

### Étape 1 : Préparation de l'environnement AWS

- Se connecter à la console AWS.
- Vérifier la région utilisée.
- Préparer les services nécessaires au projet.

### Étape 2 : Configuration de DynamoDB

- Créer les tables nécessaires.
- Définir les clés de chaque table.
- Vérifier les accès des fonctions Lambda.

### Étape 3 : Déploiement des fonctions Lambda

- Préparer les fonctions du backend.
- Configurer les variables d'environnement.
- Associer les rôles IAM.
- Déployer les fonctions.
- Vérifier leur fonctionnement dans AWS Lambda.

### Étape 4 : Configuration d'API Gateway

- Créer une API.
- Définir les différentes routes.
- Associer les routes aux fonctions Lambda.
- Configurer les paramètres CORS.
- Déployer l'API.

### Étape 5 : Hébergement sur Amazon S3

- Créer un bucket S3.
- Préparer la version de production du frontend.
- Envoyer les fichiers dans le bucket.
- Configurer les paramètres d'accès.
- Vérifier l'accessibilité du site.

### Étape 6 : Configuration de CloudFront

- Créer une distribution CloudFront.
- Associer le bucket S3 comme origine.
- Configurer le cache.
- Activer HTTPS.
- Tester l'URL de la distribution.

### Étape 7 : Tests

- Tester l'inscription et la connexion.
- Tester la création d'événements.
- Tester les réservations.
- Tester l'annulation des réservations.
- Vérifier les données dans DynamoDB.
- Consulter les logs CloudWatch.
- Tester l'accès au site.

## 8. Sécurité du projet

La sécurité est un élément essentiel du projet.

Les mesures prévues sont :

- Création d'un rôle IAM pour Lambda.
- Application du principe du moindre privilège.
- Protection des informations sensibles.
- Utilisation des variables d'environnement.
- Vérification du fichier .gitignore.
- Configuration des permissions S3.
- Configuration CORS.
- Utilisation du protocole HTTPS avec CloudFront.

Aucune clé d'accès ou aucun mot de passe ne doit être enregistré directement dans le code source.

## 9. Versioning et restauration

Le versioning Amazon S3 permet de conserver plusieurs versions d'un même fichier.

Il permet notamment :
- De retrouver une ancienne version d'un fichier.
- De récupérer un fichier supprimé accidentellement.
- De restaurer une version précédente.

Une démonstration de restauration sera réalisée afin de vérifier le fonctionnement de cette fonctionnalité.

## 10. Gestion du budget et des coûts

AWS Budgets permet de surveiller les dépenses liées aux ressources utilisées.

Les services retenus pour le projet sont :

- AWS Lambda.
- Amazon DynamoDB.
- Amazon API Gateway.
- Amazon S3.
- Amazon CloudFront.

Afin d'éviter les dépenses inutiles, le groupe évite la création de ressources facturées à l'heure telles que EC2 et RDS.

La consommation des services doit être surveillée régulièrement.

## 11. Répartition des responsabilités

Le projet est réalisé par un groupe de six membres.

| Membre | Responsabilité |
|---|---|
| Membre 1 | Frontend : pages, navigation et formulaires |
| Membre 2 | Backend : Lambda et DynamoDB |
| Membre 3 | Infrastructure : versioning S3 et budget |
| Membre 4 | Sécurité : IAM et permissions |
| Membre 5 | Documentation : README et architecture |
| Membre 6 | Bonus : CloudFront et HTTPS |

Chaque membre est responsable de la réalisation de sa partie et doit fournir les preuves de son travail.

## 12. Suivi des contributions Git

Chaque membre doit effectuer des commits réguliers sur GitHub ou GitLab.

Exemples de messages de commits :

```text
feat: Création de la page d'accueil
feat: Implémentation de la fonction Lambda register
fix: Correction du bug de réservation
docs: Mise à jour du README
```

Les captures d'écran des commits permettront de vérifier les contributions individuelles.

## 13. Démonstration du projet

La démonstration finale est prévue sur une durée de 10 minutes.

### Présentation de l'architecture (2 minutes)

- Expliquer l'architecture globale.
- Présenter les services AWS utilisés.
- Montrer le diagramme d'architecture.

### Questions techniques (4 minutes)

Chaque membre répond à deux questions concernant sa partie.

### Démonstration en direct (4 minutes)

- Création d'un compte utilisateur.
- Création d'un événement.
- Réservation de places.
- Annulation d'une réservation.
- Vérification des données dans DynamoDB.

## 14. Liens du projet

**Dépôt GitHub :** À compléter.

**URL du site déployé :** À compléter.

**URL HTTPS CloudFront :** À compléter après configuration.

## 15. Conclusion

Le projet EventPRT permet de mettre en pratique les notions fondamentales du Cloud Computing à travers la conception et le déploiement d'une application web basée sur les services AWS.

Il permet notamment de comprendre l'hébergement Cloud, le traitement des requêtes, le stockage des données, la sécurité des ressources, le versioning et la gestion des coûts.

La réalisation de ce projet repose sur la collaboration des six membres du groupe, chacun intervenant dans un domaine précis afin de garantir le bon fonctionnement de la plateforme.
