# Etapa de desarrollo
FROM node:18-alpine AS base
WORKDIR /app

# Etapa de desarrollo (Node.js y React en vivo)
FROM base AS dev
EXPOSE 3000  


# Etapa de producción con Node.js y Nginx
FROM node:18-alpine AS prod
WORKDIR /app

# Instalamos Nginx en la imagen de Node.js
RUN apk add --no-cache nginx

# Configurar el directorio de Nginx
RUN mkdir -p /run/nginx /usr/share/nginx/html

# Exponer puerto HTTP
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
