FROM php:8.2-apache

#install some basic tools
RUN apt update && apt install sudo git wget software-properties-common -y

#install some base extensions
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN apt update && apt upgrade -y

#setup composer 
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/ && ln -s /usr/local/bin/composer.phar /usr/local/bin/composer

EXPOSE 80

RUN a2enmod rewrite

#ssh access
RUN apt update && apt install openssh-server -y
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 jrichmond 
RUN  echo 'jrichmond:Testing123!' | chpasswd
RUN service ssh start
EXPOSE 22
CMD ["/usr/sbin/sshd","-D"]


# Install code sniffer
RUN pear install pear/PHP_CodeSniffer

# Checkout Wordpress standards (0.10.0)
RUN git clone git://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git $(pear config-get php_dir)/PHP/CodeSniffer/Standards/WordPress && (cd $(pear config-get php_dir)/PHP/CodeSniffer/Standards/WordPress; git checkout tags/0.10.0) && phpcs --config-set installed_paths $(pear config-get php_dir)/PHP/CodeSniffer/Standards/WordPress && phpcs --config-set default_standard WordPress

VOLUME /wordpress
WORKDIR /wordpress

CMD ["phpcs", "."]