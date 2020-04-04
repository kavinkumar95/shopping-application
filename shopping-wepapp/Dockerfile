FROM node:10-alpine AS builder

WORKDIR /src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build-prod

FROM nginx:1.13.12-alpine

COPY --from=builder /src/app/dist /etc/nginx/html

COPY ./nginx.conf /etc/nginx/nginx.conf