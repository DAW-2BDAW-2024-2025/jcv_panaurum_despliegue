# Etapa de desarrollo
FROM node:18-alpine AS dev
WORKDIR /app

# Etapa de producción con Nginx
FROM nginx:alpine AS prod
WORKDIR /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
