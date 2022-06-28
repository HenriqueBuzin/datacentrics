# build
FROM node:alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# deploy
FROM nginx
EXPOSE 80
COPY ./config/nginx.conf /etc/nginx/conf.d/default.conf
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist/ /var/www/html/