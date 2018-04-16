FROM php:7.2-fpm
MAINTAINER kan
RUN apt-get update && docker-php-ext-install pdo_mysql mysqli
RUN apt-get install wget
RUN apt-get install -y vim
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

# ADD ./setting/php7/php.ini /usr/local/etc/php/
# RUN chmod 755 /usr/local/etc/php/php.ini

WORKDIR /var/www