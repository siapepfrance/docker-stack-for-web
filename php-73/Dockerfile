FROM ubuntu:18.04
ARG TIMEZONE=Europe/France
ARG DEBIAN_FRONTEND=noninteractive

COPY php.ini /etc/php/7.3/fpm/php.ini
ADD conf/www.conf /etc/php/7.3/fpm/pool.d/www.conf
ADD conf/php-fpm.conf /etc/php/7.3/fpm/php-fpm.conf

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common && DEBIAN_FRONTEND=noninteractive add-apt-repository ppa:ondrej/php && DEBIAN_FRONTEND=noninteractive apt-get install -my \
  curl \
  wget \
  php7.3-curl \
  php7.3-fpm \
  php7.3-gd \
  php7.3-xsl \
  php7.3-mysqlnd \
  php7.3-cli \
  php7.3-intl \
  php7.3-bz2 \
  php7.3-zip \
  php7.3-mbstring \
  git \
  zip \
  php7.3-apcu \
  php7.3-redis \
  php7.3-opcache \
  php7.3-soap
RUN mkdir /run/php

# Set timezone
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone \
    && printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini \
    && "date"

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/symfony