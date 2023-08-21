# Use the official Alpine Linux base image
FROM alpine:latest

# Set environment variables to configure PHP
ENV PHP_VERSION=5.6 \
    PHP_INI_DIR=/etc/php5 \
    APACHE_RUN_USER=www-data \
    APACHE_RUN_GROUP=www-data \
    APACHE_LOG_DIR=/var/log/apache2

# Install Apache, PHP 5.6, and common PHP extensions
RUN apk --no-cache add \
        apache2 \
        apache2-utils \
        php5-apache2 \
        php5-mysql \
        php5-mysqli \
        php5-pdo_mysql \
        php5-pdo_sqlite \
        php5-xml \
        php5-gd \
        php5-curl \
        php5-json \
        php5-openssl \
        php5-zip \
        php5-zlib \
        php5-phar \
        php5-dom \
        php5-xmlreader \
        php5-ctype \
        php5-mcrypt \
        php5-iconv \
        php5-simplexml \
        php5-tokenizer \
        php5-xmlwriter \
        php5-session \
        php5-opcache

# Configure Apache
RUN mkdir -p /run/apache2 && \
    sed -i 's/#LoadModule\ rewrite_module/LoadModule\ rewrite_module/' /etc/apache2/httpd.conf && \
    sed -i 's/AllowOverride\ None/AllowOverride\ All/' /etc/apache2/httpd.conf && \
    echo "ServerName localhost" >> /etc/apache2/httpd.conf

# Create a PHP info page for testing
RUN echo "<?php phpinfo(); ?>" > /var/www/localhost/htdocs/phpinfo.php

# Expose ports
EXPOSE 80

# Start Apache
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
