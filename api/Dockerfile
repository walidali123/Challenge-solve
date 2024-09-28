# Use the official PHP image with Apache
FROM php:8.1-apache

# Install necessary PHP extensions for Laravel
RUN apt-get update && apt-get install -y \
    libzip-dev unzip git curl \
    && docker-php-ext-install pdo pdo_mysql zip \
    && a2enmod rewrite

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html

# Copy the application code
COPY . .

# Ensure correct permissions for storage and bootstrap/cache
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Install Laravel dependencies via Composer
RUN composer install --no-interaction --prefer-dist --optimize-autoloader

# Expose port 8000 for the Laravel app
EXPOSE 8000

# Run Apache in the foreground
CMD ["apache2-foreground"]
