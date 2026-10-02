# Render.com Dockerfile for Laravel + React (Inertia.js)
FROM php:8.3-fpm-alpine

# Install system dependencies
RUN apk add --no-cache \
    nginx \
    nodejs \
    npm \
    postgresql-dev \
    git \
    curl \
    libpng-dev \
    oniguruma-dev \
    libxml2-dev \
    zip \
    unzip

# Install PHP extensions
RUN docker-php-ext-install pdo pdo_pgsql mbstring exif pcntl bcmath gd

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /app

# Copy application files
COPY . /app

# Install dependencies
RUN composer install --no-dev --optimize-autoloader --no-interaction
RUN npm ci
RUN npm run build

# Setup Laravel
RUN php artisan config:cache && \
    php artisan route:cache && \
    php artisan view:cache

# Setup permissions
RUN chown -R www-data:www-data /app/storage /app/bootstrap/cache

# Configure Nginx
COPY docker/nginx.conf /etc/nginx/http.d/default.conf

# Expose port
EXPOSE 10000

# Start services
CMD php artisan migrate --force && \
    php-fpm -D && \
    nginx -g 'daemon off;'
