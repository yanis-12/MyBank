FROM php:8.2-fpm

# Installe les extensions PHP nécessaires
RUN apt-get update && apt-get install -y \
    git\
    libicu-dev \
    libpq-dev \
    libzip-dev \
    unzip \
    && docker-php-ext-install intl pdo pdo_mysql zip

# Installe Composer
COPY --from=composer:2.6 /usr/bin/composer /usr/bin/composer

# Configure le répertoire de travail
WORKDIR /app

# Copie des fichiers du projet Symfony
COPY . .

# Installe les dépendances Symfony
RUN composer install --no-dev --optimize-autoloader

# Définit le port exposé
EXPOSE 8000

# Commande par défaut pour démarrer le serveur Symfony
CMD ["php", "-S", "0.0.0.0:8000", "-t", "public"]
