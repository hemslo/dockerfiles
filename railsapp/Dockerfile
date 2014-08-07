FROM ubuntu
MAINTAINER Hemslo Wang <hemslo.wang@gmail.com>

RUN apt-get update
RUN apt-get install -y openssh-server supervisor git-core \
        curl autoconf bison zlib1g zlib1g-dev build-essential \
        libssl-dev libreadline-dev libreadline6 libreadline6-dev \
        libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev \
        libcurl4-openssl-dev software-properties-common

# Install Ruby
RUN git clone https://github.com/sstephenson/ruby-build.git /root/ruby-build
RUN cd /root/ruby-build && ./install.sh
RUN ruby-build 2.1.2 /usr/local
RUN gem install bundler

# Install Nginx & Node.js
RUN add-apt-repository -y ppa:nginx/stable
RUN add-apt-repository -y ppa:chris-lea/node.js
RUN apt-get update
RUN apt-get install -y nginx nodejs

COPY nginx.conf /etc/nginx/nginx.conf

# Install bower
RUN npm install -g bower

# Add deployer user
RUN adduser --disabled-password --home=/home/deployer deployer
gg
RUN mkdir -p /var/run/sshd
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

# Supervisor
COPY supervisord.conf /etc/supervisor/supervisord.conf

VOLUME ["/data", "/etc/nginx/sites-enabled", "/var/log/nginx", "/etc/supervisor/conf.d", "/var/log/supervisor", "/home/deployer/.ssh"]

EXPOSE 22 80

CMD ["/usr/bin/supervisord"]

