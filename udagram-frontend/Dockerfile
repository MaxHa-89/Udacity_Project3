FROM node:13 as build
WORKDIR /app
COPY package*.json /app/
RUN npm ci
RUN npm install
COPY ./ /app/
RUN npm install -g @ionic/cli
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /app/www/ /usr/share/nginx/html/
