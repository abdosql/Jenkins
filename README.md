# Pipeline CI/CD pour Symfony avec Jenkins

## 📝 Description du Projet

Dans le cadre de ce projet, j'ai mis en place un pipeline d'intégration et de déploiement continu (CI/CD) pour une application Symfony en utilisant Jenkins et Docker. L'objectif était d'automatiser complètement le processus de développement, de test et de déploiement.

## 🛠️ Technologies Utilisées

- **Jenkins**: Pour l'automatisation du pipeline CI/CD
- **Docker**: Pour la conteneurisation de l'environnement
- **Symfony CLI**: Pour la création et la gestion du projet Symfony
- **PHP**: Comme langage de programmation principal
- **Composer**: Pour la gestion des dépendances PHP

## 🔄 Fonctionnement du Pipeline

J'ai configuré un pipeline Jenkins qui exécute automatiquement les étapes suivantes :

1. **Installation et Configuration (Setup)**
   - Installation automatique de Symfony CLI
   - Création d'un nouveau projet Symfony
   - Installation des packages nécessaires

2. **Construction (Build)**
   - Installation des dépendances via Composer
   - Préparation de l'application pour le déploiement

3. **Tests**
   - Exécution des tests unitaires avec PHPUnit
   - Vérification de la qualité du code

4. **Déploiement**
   - Démarrage du serveur Symfony
   - Mise en ligne de l'application

## 📁 Structure du Projet

```
.
├── Jenkinsfile              # Configuration du pipeline
├── docker-compose.yml       # Configuration des services Docker
├── docker/
│   ├── jenkins/            
│   │   └── Dockerfile      # Configuration conteneur Jenkins
│   └── php/
│       └── Dockerfile      # Configuration conteneur PHP
└── symfony/                # Application Symfony
```

## 🔧 Améliorations Apportées

1. **Automatisation Complète**
   - Utilisation de Symfony CLI pour une installation standardisée
   - Configuration automatique de l'environnement de développement

2. **Environnement Isolé**
   - Utilisation de Docker pour garantir la cohérence entre les environnements
   - Configuration précise des conteneurs pour les besoins spécifiques

3. **Sécurité et Maintenabilité**
   - Séparation des configurations sensibles
   - Structure modulaire facilitant les mises à jour

## 📈 Compétences Développées

- Configuration et gestion d'un pipeline CI/CD
- Utilisation avancée de Docker et conteneurisation
- Automatisation des processus de développement
- Gestion de projet avec des outils modernes
- Intégration de tests automatisés

## 🎯 Objectifs Atteints

- Mise en place d'un pipeline CI/CD fonctionnel
- Automatisation complète du processus de déploiement
- Environnement de développement standardisé
- Tests automatisés intégrés au processus

## 🆕 Dernières Mises à Jour (22/12/2024)

### 1. Image Docker Unifiée
- Création d'une image Docker unique combinant Jenkins et Symfony
- Image disponible sur Docker Hub : `seqqal/jenkins-symfony:latest`
- Simplification du déploiement avec une configuration tout-en-un

### 2. Améliorations de l'Environnement
- Installation de PHP 8.2 avec toutes les extensions nécessaires
- Configuration automatique de Composer et Symfony CLI
- Permissions optimisées pour l'utilisateur Jenkins

### 3. Utilisation Simplifiée
Pour utiliser cette configuration :
```bash
# Télécharger l'image
docker pull seqqal/jenkins-symfony:latest

# Démarrer avec docker-compose
docker-compose up -d
```

### 4. Fonctionnalités Incluses dans l'Image
- Jenkins LTS préconfiguré
- PHP 8.2 avec extensions (cli, fpm, mysql, zip, gd, mbstring, curl, xml, bcmath)
- Composer pour la gestion des dépendances
- Symfony CLI pour le développement
- Structure de répertoires préparée pour les projets Symfony
