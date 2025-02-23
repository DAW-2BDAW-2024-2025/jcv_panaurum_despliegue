FROM php:8.2-apache

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl \
    libpq-dev \
    libonig-dev \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    openssl \
    zlib1g-dev \
    supervisor

# Instalar extensiones de PHP necesarias para Laravel
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && docker-php-ext-install mysqli pdo pdo_mysql zip

# Instalar Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# Configurar directorio de trabajo
WORKDIR /var/www

# Asegurar que www-data tenga el mismo UID y GID que el usuario del host
#RUN usermod -u 1000 www-data && groupmod -g 1000 www-data

# Ajustar permisos para evitar problemas con volúmenes montados
#RUN chown -R www-data:www-data /var/www

# Habilitar mod_rewrite para Laravel
RUN a2enmod rewrite

# Configurar Opcache (mejora el rendimiento de PHP)
#RUN docker-php-ext-install opcache
#COPY opcache.ini /usr/local/etc/php/conf.d/opcache.ini

# Habilitar el puerto 8000 en Apache
RUN echo "Listen 8000" >> /etc/apache2/ports.conf \
    && sed -i 's/<VirtualHost \*:80>/<VirtualHost *:8000>/' /etc/apache2/sites-available/000-default.conf

# Asegurar que el VirtualHost esté habilitado y activo
RUN a2ensite 000-default.conf

# Exponer el puerto correcto para Apache
EXPOSE 8000

# Comando de inicio
CMD ["apache2-foreground"]
