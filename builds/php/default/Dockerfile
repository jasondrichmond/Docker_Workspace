FROM php:8.2.14-fpm

#install some basic tools
RUN apt update && apt install sudo git wget software-properties-common -y

#install some base extensions
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN apt update && apt upgrade -y

#setup composer 
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/ && ln -s /usr/local/bin/composer.phar /usr/local/bin/composer

WORKDIR /var/www/html

EXPOSE 80

#RUN a2enmod rewrite

#ssh access
RUN apt update && apt install openssh-server -y
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 jrichmond 
RUN echo 'root:Docker!' | chpasswd
RUN service ssh start
EXPOSE 22
CMD ["/usr/sbin/sshd","-D"]

