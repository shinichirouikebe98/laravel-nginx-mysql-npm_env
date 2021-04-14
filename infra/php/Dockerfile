FROM php:8.0.3-fpm

SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

#composer install
COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

#その他パッケージ
RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath

#npm instal
RUN curl -sL https://deb.nodesource.com/setup_15.x | bash -
RUN apt-get install -y nodejs

 

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /work