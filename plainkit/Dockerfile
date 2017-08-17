# based on php apache offical
FROM php:7-apache

# update, install & clean up
RUN apt-get update && apt-get install -y \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng12-dev \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install -j$(nproc) gd  \
  && rm -rf /var/lib/apt/lists/*

# copy default apache conf
COPY 000-default.conf /etc/apache2/sites-enabled

# enable rewrites & restart apache
RUN a2enmod rewrite \
    && service apache2 restart

# set working directory
WORKDIR /var/www/html/

# copy kirby
COPY plainkit/ ./

# create thumbs folder and set permissions for kirby
RUN mkdir /var/www/html/thumbs \
  && chown -R www-data:www-data /var/www/html \
  && chmod -R 755 /var/www/html/thumbs

# expose kirby directories
VOLUME ["/var/www/html/content", "/var/www/html/assets", "/var/www/html/site"]
