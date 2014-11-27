FROM ubuntu:14.04
RUN apt-get update && apt-get install -y \
    git-core curl autoconf bison  zlib1g-dev build-essential \
    libcurl4-openssl-dev libncurses5-dev libreadline-dev libreadline6-dev \
    libssl-dev libxml2-dev libxslt1-dev libyaml-dev libsqlite3-dev sqlite3 \
    libmysqlclient-dev python-software-properties software-properties-common

# Install Ruby
RUN git clone https://github.com/sstephenson/ruby-build.git /root/ruby-build
RUN cd /root/ruby-build && ./install.sh
RUN ruby-build 2.1.5 /usr/local
RUN gem install bundler

RUN curl -sL https://deb.nodesource.com/setup | bash -
RUN apt-get update && apt-get install -y nodejs

RUN npm install -g bower

RUN mkdir /data

WORKDIR /data

EXPOSE 3000

CMD ["bundle", "exec", "rails", "s"]
