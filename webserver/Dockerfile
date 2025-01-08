# Étape 1 : Construire l'application React avec Vite
FROM node:lts-alpine3.12 as build

# Définir le répertoire de travail
WORKDIR /lexydocs

# Copier les fichiers de dépendances
COPY package.json package-lock.json ./

# Installer les dépendances
RUN npm install

# Copier le reste des fichiers du projet
COPY . .

# Construire l'application React avec Vite
RUN npm run build

# Étape 2 : Servir l'application avec Nginx
FROM nginx:1.18.0-alpine

# Copier les fichiers construits par Vite
COPY --from=build /lexydocs/dist /usr/share/nginx/html/frontend1

# Exposer le port 80
EXPOSE 80

# Démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]