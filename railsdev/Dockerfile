FROM ubuntu
MAINTAINER Hemslo Wang <hemslo.wang@gmail.com>

RUN apt-get update && apt-get install -y \
    git-core curl autoconf bison zlib1g zlib1g-dev build-essential libssl-dev \
    libreadline-dev libreadline6 libreadline6-dev libncurses5-dev libyaml-dev \
    libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev \
    software-properties-common python-software-properties libmysqlclient-dev

# Install Ruby
RUN git clone https://github.com/sstephenson/ruby-build.git /root/ruby-build
RUN cd /root/ruby-build && ./install.sh
RUN ruby-build 2.1.3 /usr/local
RUN gem install bundler

RUN curl -sL https://deb.nodesource.com/setup | bash -
RUN apt-get update && apt-get install -y nodejs

RUN npm install -g bower

RUN mkdir /data

WORKDIR /data

EXPOSE 3000

CMD ["bundle", "exec", "rails", "s"]
