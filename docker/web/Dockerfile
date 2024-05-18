FROM php:8.1-apache AS app_php

# Change docroot
ENV APACHE_DOCUMENT_ROOT /var/www/html/
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# Add configs
COPY ./docker/web/configs/apache/sites-enabled/* /etc/apache2/sites-enabled/

# php extensions installer: https://github.com/mlocati/docker-php-extension-installer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

# install composer
COPY --from=composer/composer:2-bin /composer /usr/bin/composer

# Install php extensions
RUN set -eux; \
    install-php-extensions \
        xdebug \
    ;

# Copy custom configs into place
COPY docker/web/configs/php/*.ini $PHP_INI_DIR/conf.d/

# Enable Apache mods
RUN a2enmod ssl \
    && a2enmod allowmethods \
    && a2enmod headers \
    && a2enmod mime \
    && a2enmod rewrite

