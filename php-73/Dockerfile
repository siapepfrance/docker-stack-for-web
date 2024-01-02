FROM php:7.3-fpm-alpine
ARG TIMEZONE=Europe/Paris

COPY init.sh /
COPY php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

RUN apk update \
    && apk add bash git openssh ca-certificates wget freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev postgresql-dev libxml2-dev \
    && docker-php-ext-install gd pdo pdo_mysql pdo_pgsql pgsql xml soap \
    && rm /var/cache/apk/*

RUN mkdir /run/php

# Set timezone
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone \
    && printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini \
    && "date"

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/app
RUN chmod +x /init.sh
CMD /init.sh