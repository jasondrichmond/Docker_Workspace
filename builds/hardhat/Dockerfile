# Dockerfile
FROM ubuntu:latest
WORKDIR /app
RUN mkdir /var/run/sshd

RUN apt-get update && apt-get install -y \
    curl \
    openssh-client \
	openssh-server \
    wget \
	vim \
	npm

RUN echo 'root:Docker!' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

ADD . /app

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]