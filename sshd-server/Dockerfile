FROM ubuntu:12.04
MAINTAINER ICHIMURA Yuichi

RUN apt-get update
# install sshd
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

# useradd
RUN useradd --create-home -s /bin/bash y16ra; echo "y16ra:pass123" | chpasswd

# launch sshd
EXPOSE 22
ENTRYPOINT ["/usr/sbin/sshd","-D"]

