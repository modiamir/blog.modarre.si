FROM php:7.2-fpm

RUN docker-php-ext-install pdo_mysql
RUN apt-get update \
    && apt install -y mysql-client

RUN apt install -y libxml2-dev \
    && docker-php-ext-install xml

RUN apt-get install -y libpng-dev
RUN docker-php-ext-install gd


RUN docker-php-ext-install zip

RUN curl -s http://getcomposer.org/installer | php && \
    echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
    mv composer.phar /usr/local/bin/composer

RUN docker-php-ext-install bcmath

RUN apt install -y git

RUN docker-php-ext-install opcache

ENV TZ=Asia/Tehran
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY php.ini /usr/local/etc/php/

RUN usermod -u 1000 www-data
RUN groupmod -g 1000 www-data
WORKDIR /var/www/app
USER www-data