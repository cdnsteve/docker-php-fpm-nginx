FROM alpine:3.2
MAINTAINER Steven Leggett <leggettsteven@gmail.com>

ENV BUILD_PACKAGES bash curl wget git
ENV PHP_PACKAGES php-fpm php-curl php-openssl php-json php-phar php-dom \
    php-gd php-xml 

# Update and install all of the required packages.
# At the end, remove the apk cache
RUN apk update && \
    apk upgrade && \
    apk add $BUILD_PACKAGES && \
    apk add $PHP_PACKAGES && \
    rm -rf /var/cache/apk/*
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer 

COPY php-fpm.conf /etc/php/

EXPOSE 9000
CMD ["php-fpm"]

