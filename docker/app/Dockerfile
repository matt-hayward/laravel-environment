FROM php:7.2-fpm

#ARG uid=999
#RUN usermod -u $uid www-data

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y openssl zlib1g-dev zip unzip git nano
RUN docker-php-ext-install pdo pdo_mysql bcmath zip

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
RUN mkdir /var/www/.composer
RUN chmod -R 0775 /var/www/.composer
RUN mkdir /var/www/.ssh
RUN chmod -R 0775 /var/www/.ssh

WORKDIR /var/www/html
