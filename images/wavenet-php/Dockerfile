FROM php:8.1-apache

RUN echo "Building the PHP specific"

RUN a2enmod rewrite

RUN apt-get update
RUN apt-get install -y git libfreetype6-dev libjpeg62-turbo-dev libpng-dev zip unzip zlib1g-dev libicu-dev g++ libzip-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql intl zip bcmath gd && docker-php-ext-enable pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apt-get install -y openssh-server systemctl
RUN systemctl enable ssh

RUN echo 'root:pass' | chpasswd
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
RUN sed -i 's/PermitRootLogin password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN useradd -m -s /bin/bash sshuser
RUN echo "sshuser:Changeme" | chpasswd

RUN chmod 777 -R /var/www/html

EXPOSE 22

COPY docker-php-wavenet-entrypoint /usr/local/bin/

CMD [ "docker-php-wavenet-entrypoint" ]