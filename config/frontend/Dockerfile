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

# Eliminamos el archivo de configuración por defecto de Nginx (solo si existe)
RUN rm -f /etc/nginx/conf.d/default.conf

# Copiar el archivo de configuración de producción de Nginx
#COPY nginx.prod.conf /etc/nginx/conf.d/default.conf

# Configurar el directorio de Nginx
RUN mkdir -p /run/nginx /usr/share/nginx/html

# Exponer puerto HTTP
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
