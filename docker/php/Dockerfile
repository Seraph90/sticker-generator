FROM composer:2.6.5 as composer
FROM php:8.3.0-fpm
COPY --from=composer /usr/bin/composer /usr/bin/composer

LABEL maintainer="Alex Heifetz <seraph90seraph@gmail.com>"

RUN apt-get update
RUN apt-get install -y apt-utils net-tools nano htop

COPY files/php.ini /usr/local/etc/php/conf.d/php.ini

RUN pecl install xdebug && docker-php-ext-enable xdebug
COPY files/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

COPY files/docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
