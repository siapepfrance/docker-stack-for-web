FROM php:8.4-fpm-alpine
ARG TIMEZONE=Europe/Paris

COPY php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

RUN apk update && apk add --no-cache \
    gnupg \
    g++ \
    procps \
    openssl \
    git \
    unzip \
    zlib-dev \
    libzip-dev \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    icu-dev  \
    oniguruma-dev \
    libxslt-dev \
    acl \
    linux-headers

RUN docker-php-ext-configure gd --with-jpeg --with-freetype 

RUN curl -fsSL https://xdebug.org/files/xdebug-3.4.1.tgz -o xdebug.tgz \
    && tar -xzf xdebug.tgz \
    && cd xdebug-3.4.1 \
    && phpize \
    && ./configure --enable-xdebug \
    && make \
    && make install \
    && cd .. \
    && rm -rf xdebug.tgz xdebug-3.4.1

RUN docker-php-ext-install \
    pdo pdo_mysql zip xsl gd intl opcache exif mbstring

RUN docker-php-ext-enable xdebug

# Set timezone
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone \
    && printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini \
    && "date"

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/app