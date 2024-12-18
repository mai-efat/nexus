# Step 1: Use an official PHP image with necessary extensions
FROM php:8.1-cli

# Install system dependencies and PHP extensions required by Laravel
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libzip-dev \
    git \
    curl \
    unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql bcmath opcache zip

# Step 2: Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Step 3: Set the working directory inside the container
WORKDIR /var/www/html

# Step 4: Copy the Laravel app into the container
COPY . .

# Step 5: Install Laravel PHP dependencies using Composer
RUN composer install --no-scripts --no-autoloader

# Step 6: Set up storage and cache directories permissions
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Step 7: Expose port 8000 (for the API)
EXPOSE 8000

CMD ["php", "artisan", "serve","--host=0.0.0.0","--port=8000"]