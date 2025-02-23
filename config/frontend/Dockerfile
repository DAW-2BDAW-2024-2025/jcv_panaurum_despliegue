# Etapa de desarrollo
FROM node:18-alpine AS base
WORKDIR /app

# Etapa de desarrollo (Node.js y React en vivo)
FROM base AS dev
EXPOSE 3000  


# Etapa de producción con Nginx
FROM base AS prod
WORKDIR /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
