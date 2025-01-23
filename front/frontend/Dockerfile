# Étape 1 : Build
FROM node:18 as build

# Définit le répertoire de travail dans le conteneur
WORKDIR /app

# Copie les fichiers nécessaires dans le conteneur
COPY package.json package-lock.json ./

# Installe les dépendances
RUN npm install

# Copie tout le reste du projet
COPY . .

# Build le projet pour la production
RUN npm run build

# Étape 2 : Serveur
FROM nginx:stable-alpine

# Copie les fichiers construits dans le répertoire nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expose le port 80
EXPOSE 80

# Commande pour lancer Nginx
CMD ["nginx", "-g", "daemon off;"]
