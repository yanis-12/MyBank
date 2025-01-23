                         Déploiement du Frontend




Ce guide explique comment déployer le frontend de l'application en utilisant Docker.
Technologies utilisées

    Framework : React

    Gestionnaire de packages : npm

    Conteneurisation : Docker

    Serveur web : Nginx

Prérequis

Avant de commencer, assurez-vous d'avoir installé les outils suivants :

    Docker :

        Téléchargez et installez Docker depuis docker.com.

        Vérifiez l'installation avec :
        bash
        Copy

        docker --version
        docker-compose --version

    Git (pour cloner le dépôt) :

        Téléchargez et installez Git depuis git-scm.com.

        Vérifiez l'installation avec :
        bash
        Copy

        git --version

Déployer le Frontend avec Docker
1. Cloner le dépôt

Clonez le dépôt du projet si ce n'est pas déjà fait :
bash
Copy

git clone https://github.com/yanis-12/MyBank
cd mybank-frontend

1. Construire l'image Docker

Le fichier Dockerfile est déjà configuré pour construire et déployer l'application. Voici ce qu'il fait :

    Étape 1 : Build

        Utilise une image Node.js pour installer les dépendances et construire l'application.

        Le résultat est stocké dans le dossier /app/dist.

    Étape 2 : Serveur

        Utilise une image Nginx pour servir les fichiers construits.

        Les fichiers sont copiés dans le répertoire Nginx (/usr/share/nginx/html).

Pour construire l'image Docker, exécutez la commande suivante :
bash
Copy

docker build -t mybank-frontend .

3. Lancer le conteneur

Une fois l'image construite, vous pouvez lancer le conteneur avec la commande suivante :
bash
Copy

docker run -d -p 3000:80 --name mybank-frontend mybank-frontend

Explication des options :

    -d : Lance le conteneur en mode détaché (en arrière-plan).

    -p 3000:80 : Expose le port 80 du conteneur sur le port 3000 de votre machine.

    --name mybank-frontend : Donne un nom au conteneur.

    mybank-frontend : Nom de l'image Docker à utiliser.

4. Accéder à l'application

Une fois le conteneur lancé, l'application sera accessible à l'adresse suivante :
Copy

http://localhost:3000