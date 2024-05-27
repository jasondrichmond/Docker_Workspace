FROM php:7.4-apache

RUN apt-get update -y && \
    apt-get install -y curl unzip openssh-server wget sudo && \
    a2enmod rewrite
    
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 jrichmond 
RUN echo 'root:Docker!' | chpasswd
RUN service ssh start

EXPOSE 80
EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
