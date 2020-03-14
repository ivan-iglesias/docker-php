ARG VERSION
FROM php:${VERSION}

RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev && \
    docker-php-ext-install \
        zip \
        intl \
        mysqli \
        pdo pdo_mysql

# Install composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# Configure non-root user
ARG PUID=1000
ENV PUID ${PUID}
ARG PGID=1000
ENV PGID ${PGID}
RUN useradd -G www-data,root -u $PUID -d /home/devuser devuser && \
    mkdir -p /home/devuser/.composer && \
    chown -R devuser:devuser /home/devuser
USER devuser

# Alias
ARG APP_FRAMEWORK="laravel"
ENV APP_FRAMEWORK ${APP_FRAMEWORK}

RUN if [ "$APP_FRAMEWORK" = "laravel" ]; then \
    echo 'alias pa="php artisan "' >> ~/.bashrc && \
    echo 'alias pt="vendor/bin/phpunit "' >> ~/.bashrc \
;fi
RUN if [ "$APP_FRAMEWORK" = "symfony" ]; then \
    echo 'alias sf="php bin/console "' >> ~/.bashrc && \
    echo 'alias st="php bin/phpunit "' >> ~/.bashrc \
;fi

# Set working directory
ARG APP_NAME
COPY src/ /var/www/${APP_NAME}
WORKDIR /var/www/${APP_NAME}/
