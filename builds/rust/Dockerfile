# 1. This tells docker to use the Rust official image
FROM rust:1.49

# 2. Copy the files in your machine to the Docker image
COPY ./holodeck ./

# Build your program for release
# RUN cargo build --release

RUN apt-get update -y && \
    apt-get install -y curl unzip openssh-server wget sudo

# Enable SSH
RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 jrichmond 
RUN echo 'root:Docker!' | chpasswd
RUN service ssh start

EXPOSE 80
EXPOSE 22

# Run the binary
#CMD ["./target/release/holodeck"]
CMD ["/usr/sbin/sshd","-D"]