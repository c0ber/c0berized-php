FROM php:7.2-fpm

WORKDIR /app

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libicu-dev \
        libpcre3-dev \
        libcurl3-dev\
        curl\
        git \
    && docker-php-ext-install -j$(nproc) iconv mbstring intl opcache curl pdo zip pdo_mysql curl json \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && pecl install xdebug-2.6.0beta1 \
    && docker-php-ext-enable xdebug

COPY xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

ENV COMPOSER_HOME /root/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH
RUN composer global require hirak/prestissimo friendsofphp/php-cs-fixer
