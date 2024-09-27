# Use the official PHP image with Apache
FROM php:8.1-apache

# Install necessary extensions
RUN docker-php-ext-install pdo pdo_mysql

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html

# Copy the application code
COPY . .

# Install dependencies
RUN composer install

# Expose port 8000 for the Laravel app
EXPOSE 8000

# Set permissions for the storage and bootstrap/cache directories
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Run Apache in the foreground
CMD ["apache2-foreground"]
