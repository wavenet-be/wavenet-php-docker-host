FROM php:8.1-apache

RUN echo "Building the PHP specific"

RUN a2enmod rewrite

RUN apt-get update
#RUN apt-get install -y git libfreetype6-dev libjpeg62-turbo-dev libpng-dev zip unzip zlib1g-dev libicu-dev g++ libzip-dev

#RUN docker-php-ext-install mysqli pdo pdo_mysql intl zip bcmath gd && docker-php-ext-enable pdo_mysql

#RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


RUN apt-get install -y proftpd systemctl
RUN systemctl enable proftpd

RUN addgroup ftpgroup
RUN adduser ftpuser -home /var/www/html
RUN adduser ftpuser ftpgroup
RUN echo "ftpuser:Changeme" | chpasswd

COPY proftpd.conf /etc/proftpd.conf

RUN chmod -R 777 /var/www/html

EXPOSE 21