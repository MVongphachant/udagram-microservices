FROM node:18-alpine as ionic

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm ci && npm install -g @ionic/cli

COPY . .
RUN ionic build

FROM nginx:alpine

COPY --from=ionic /usr/src/app/www /usr/share/nginx/html