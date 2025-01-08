FROM node:18-alpine as build1

WORKDIR /lexydocs
COPY ./lexydocs/package.json ./
COPY ./lexydocs/package-lock.json ./
RUN npm install
COPY ./lexydocs/ ./
RUN npm run build


FROM nginx:1.18.0-alpine

# Copie de la con figuration Nginx
COPY  ./webserver/default.conf /etc/nginx/conf.d/default.conf

# Copie des applications front-end construites
COPY --from=build1 /lexydocs/dist /usr/share/nginx/html/frontend1
