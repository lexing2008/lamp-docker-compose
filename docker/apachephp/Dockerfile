FROM php:8.1-apache

# копирование virtual hosts apache
COPY apache/hosts/* /etc/apache2/sites-available

RUN a2enmod rewrite # включаем в апаче модуль rewrite
RUN a2enmod proxy_http # включаем в апаче модуль proxy_http
RUN service apache2 restart

# установка расширения mysqli
RUN docker-php-ext-install mysqli
#RUN docker-php-ext-install pdo pdo_mysql mysqli

# установка композера
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# установка расширения
#RUN pecl install xdebug \
#    && docker-php-ext-enable xdebug

# копирование конфигов php
COPY php/conf.d/* $PHP_INI_DIR/conf.d/
