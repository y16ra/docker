FROM ubuntu:14.04
MAINTAINER ICHIMURA Yuichi

# install apps
RUN     apt-get update
RUN     apt-get install -y curl git man python make gcc g++ bzip2 -yy
RUN     apt-get install -y software-properties-common python-software-properties 
RUN     add-apt-repository ppa:chris-lea/node.js
RUN     apt-get update
RUN     apt-get install -y nodejs
RUN     npm install -g ws
RUN     npm install -g node-dev

# install chat app
RUN     cd /home; git clone https://github.com/y16ra/nearby-chat-server.git
RUN     cd /home/nearby-chat-server; npm install
ADD     dev.json /home/nearby-chat-server/config/

# Timezone Setting
RUN     echo "Asia/Tokyo" > /etc/timezone
RUN     dpkg-reconfigure -f noninteractive tzdata

# env
ENV NODE_ENV dev
ENV PORT 3000

# port
EXPOSE 3000

WORKDIR /home/nearby-chat-server
CMD ["/usr/bin/node-dev", "./bin/www"]
