# Use an official PHP-Apache runtime as a parent image
FROM php:8.2-apache

# Set working directory
WORKDIR /var/www/html

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql gd

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy composer.lock and composer.json
COPY composer.lock composer.json /var/www/html/

# Install dependencies
RUN composer install --prefer-dist --no-scripts --no-dev --optimize-autoloader

# Copy the rest of the application code
COPY . /var/www/html

# Set permissions for Laravel
RUN chown -R www-data:www-data /var/www/html

# Ensure the Apache server runs properly and can serve the index.php file
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Add DirectoryIndex to ensure index.php is recognized
RUN echo '<Directory "/var/www/html">\n    Options Indexes FollowSymLinks\n    AllowOverride All\n    Require all granted\n    DirectoryIndex index.php\n</Directory>' > /etc/apache2/sites-available/000-default.conf

# Expose port 80
EXPOSE 80

# Start Apache server
CMD ["apache2-foreground"]
