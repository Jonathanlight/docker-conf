FROM php:7.1-apache

# Apache
RUN a2enmod ssl rewrite

## Basic tools
RUN apt-get update -y &&\
    apt-get upgrade -y &&\
    apt-get install -y bash \
            curl \
            wget \
            ca-certificates \
            vim

RUN echo "GREEN='\[\e[1;32m\]'" >> /root/.bashrc &&\
    echo "reset='\[\e[0m\]'" >> /root/.bashrc &&\
    echo 'PS1="${GREEN}(docker)${reset} [\u@\h \W]\\$ "' >> /root/.bashrc

## PHP
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        libxrender1 libfontconfig libXext6 \
        libicu-dev \
        libmcrypt-dev \
        libxslt1-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j4 pdo_mysql gd mbstring bcmath zip intl opcache mcrypt xsl soap

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/app