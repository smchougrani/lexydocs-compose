FROM node:lts-alpine3.12 as build1

WORKDIR /lexydocs
COPY ./lexydocs/package.json ./
COPY ./lexydocs/package-lock.json ./
RUN npm install
COPY ./lexydocs/ ./
RUN npm run build


FROM nginx:1.18.0-alpine

# Copie de la configuration Nginx
COPY  ./webserver/default.conf /etc/nginx/conf.d/default.conf

# Copie des applications front-end construites
COPY --from=build1 /lexydocs/build /usr/share/nginx/html/frontend1