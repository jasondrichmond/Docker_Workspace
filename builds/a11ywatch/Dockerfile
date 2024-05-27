FROM mattrayner/lamp

RUN apt update && apt install openssh-server sudo wget net_tools -y

RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 jrichmond 

RUN  echo 'root:Docker!' | chpasswd

RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
