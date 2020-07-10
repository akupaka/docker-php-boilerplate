FROM php:7.4-fpm-buster
MAINTAINER Roman.K <akupaka@gmail.com>

RUN groupadd -g 1000 webapp \
 && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash webapp

# Install PHP extensions
RUN docker-php-ext-install \
  mysqli

COPY conf/www.conf /usr/local/etc/php-fpm.d/
COPY conf/php.ini /usr/local/etc/php/
COPY conf/php-fpm.conf /usr/local/etc/

RUN pecl install xdebug-2.8.1 \
 && docker-php-ext-enable xdebug

# If xdebug must be disabled on build
# RUN sed -i -e 's/^zend_extension/\;zend_extension/g' /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN mkdir -p /var/www/default/public /var/www/default/uploads /sock \
 && chown -R webapp:webapp /var/www /usr/local/etc/php/conf.d /sock
# That does not seem to be working
# && find /var/www -type f -exec chmod 444 {} \; \
# && find /var/www -type d -exec chmod 555 {} \; \
# && chmod -R 644 /var/www/default/uploads

USER webapp:webapp

VOLUME /var/www

WORKDIR /var/www

EXPOSE 9001