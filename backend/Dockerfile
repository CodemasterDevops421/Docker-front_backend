# Base image with PHP and composer
FROM php:8.1-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl

# Set working directory
WORKDIR /var/www/html

# Clone backend repository from GitHub (with authentication)
RUN git clone https://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:x-oauth-basic@github.com/Triple-Zero-pro/housemade-backend.git .

# Install PHP extensions
RUN docker-php-ext-install pdo pdo_mysql

# Install Composer (Php package manager)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install backend dependencies using Composer
RUN composer install

# Set directory permissions
RUN chmod -R ugo+rw storage/logs
RUN mkdir -p storage/framework/{sessions,views,cache}
RUN chmod -R ugo+rw storage/framework

# Start the backend application
CMD ["php", "artisan", "server", "--host=0.0.0.0"]

