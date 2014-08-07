FROM ubuntu
MAINTAINER Hemslo Wang <hemslo.wang@gmail.com>

RUN apt-get update
RUN apt-get install -y software-properties-common python-software-properties
RUN add-apt-repository -y ppa:nginx/stable
RUN add-apt-repository -y ppa:chris-lea/node.js
RUN apt-get update
RUN apt-get install -y openssh-server supervisor nginx nodejs git-core \
        autoconf bison build-essential libssl-dev libyaml-dev libreadline6 \
        libreadline6-dev zlib1g zlib1g-dev

RUN git clone https://github.com/sstephenson/ruby-build.git /root/ruby-build
RUN cd /root/ruby-build && ./install.sh
RUN ruby-build 2.1.2 /usr/local
RUN gem install bundler

RUN npm install -g bower

Add nginx.conf /etc/nginx/nginx.conf

RUN adduser --disabled-password --home=/home/deployer deployer

RUN mkdir /var/run/sshd

