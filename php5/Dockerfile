FROM srcoder/development-php:php5-fpm
MAINTAINER Jeroen Boersma <jeroen@srcode.nl>

ARG GID=1000
ARG UID=1000

RUN groupmod -g $GID app && \
    usermod -g $GID -u $UID app

ENV PHPREDIS_VERSION 2.2.8

RUN docker-php-ext-install bcmath

RUN docker-php-source extract \
    && curl -L -o /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz \
    && tar xfz /tmp/redis.tar.gz \
    && rm -r /tmp/redis.tar.gz \
    && mv phpredis-$PHPREDIS_VERSION /usr/src/php/ext/redis \
    && docker-php-ext-install redis \
    && docker-php-source delete

RUN wget https://getcomposer.org/composer.phar -O /usr/local/bin/composer \
    && chmod +x /usr/bin/composer
