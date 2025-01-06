echo "# Projet POZOS: Application Étudiante Dockerisée+hardbor+registr_prive

## Description
Le projet **POZOS** est une preuve de concept (POC) visant à déployer une **application étudiante** en utilisant **Docker** et **Docker Compose** et la gestion du registre prive avec harbor. Ce projet comprend deux composants principaux :

1. **simple_api** : Une API Flask sécurisée par authentification HTTP pour gérer un fichier JSON contenant les âges des étudiants.
2. **website** : Une application Web PHP qui interagit avec l'API pour afficher la liste des étudiants et leurs âges.

Le projet met en avant les bonnes pratiques de déploiement Docker 

---

## Objectifs
- **Dockerisation de l'application** : Simplifier le déploiement et la gestion des services.
- **Sécurité** : Implémenter une authentification HTTP pour protéger l'API.
- **Documentation complète** : Fournir des instructions claires pour la mise en place et l'utilisation.

---

## Structure du Projet

student-list-master/
├── simple_api/
│   ├── data/
│   │   ├── student_age.json
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── student_age.json
│   ├── student_age.py
├── website/
│   ├── index.php
├── docker-compose.yml
├── README.mdode de l'API Flask et le fichier de dépendances `requirements.txt`.
- **website/** : Contient le code de l'application Web PHP.

---

## Pré-requis
1. **Docker** et **Docker Compose** installés.
2. Serveur Debian configuré.
3. Accès au registre Docker privé si nécessaire.

---

## Instructions de Déploiement

### 1. Préparation de l'environnement
- Clonez le dépôt :
  
  git clone https://github.com/votre-utilisateur/student-list-master.git
  cd student-list-master
  

- Assurez-vous que Docker et Docker Compose sont installés :
 
  docker --version
  docker-compose --version
  

### 2. Création des conteneurs
- Générez les images et déployez les services :
  
  docker-compose up -d
  

### 3. Accéder à l'application
- API Flask : `http://localhost:5000`
- Application Web : `http://localhost:8080`

### 4. Test de connexion
- Connectez-vous à l'API avec une authentification HTTP.
- Assurez-vous que l'application Web peut afficher correctement les données des étudiants.

---

## Registre Docker Privé

Le projet prévoit l'utilisation d'un registre Docker privé pour gérer les images de manière sécurisée. Pour ce faire :

1. Configurez le registre Docker privé (par exemple, avec **Portus**).
2. Ajoutez l'adresse du registre dans `daemon.json` si le registre est en HTTP :
   json
   {
     "insecure-registries": ["192.168.75.131"]
   }
   
3. Poussez les images dans le registre :
   
   docker tag student-list-master-api:latest 192.168.75.131/student_project/student_api:latest
   docker push 192.168.75.131/student_project/student_api

   

---

## Bonnes Pratiques
- Utiliser HTTPS pour tout déploiement en production.
- Effectuer des tests unitaires pour valider le fonctionnement des services.
- Documenter toute modification apportée au projet.

---

## Contribution
Les contributions sont les bienvenues. Veuillez soumettre vos pull requests avec des descriptions claires des modifications apportées.

---

## Auteur
Abdoulaye Diallo
Email: agabdoulaye16@gmail.com

---

## Licence

