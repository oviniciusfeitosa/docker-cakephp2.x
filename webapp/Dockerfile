FROM php:7.3.11-apache-buster
MAINTAINER Vinicius Feitosa da Silva <viniciusfesil@gmail.com>

WORKDIR /var/www/html

COPY ./docker/conf/default.conf /etc/apache2/sites-available/000-default.conf

RUN apt-get update && \
  apt-get -y install curl git libicu-dev libpq-dev zlib1g-dev zip && \
  docker-php-ext-install intl mbstring pcntl pdo_pgsql zip && \
  usermod -u 1000 www-data && \
  usermod -a -G users www-data && \
  chown -R www-data:www-data /var/www && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
  a2enmod rewrite

COPY . /var/www/html
