FROM node:20-alpine AS build
WORKDIR /app
COPY app.js style.css index.html build.js ./
RUN node build.js

FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/dist/ /usr/share/nginx/html/
EXPOSE 80