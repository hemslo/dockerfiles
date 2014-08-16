FROM ubuntu
MAINTAINER Hemslo Wang <hemslo.wang@gmail.com>

RUN apt-get update
RUN apt-get install git-core curl zlib1g-dev build-essential libssl-dev \
        libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev \
        libxslt1-dev libcurl4-openssl-dev python-software-properties

RUN git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(rbenv init -)"' >> ~/.bashrc
RUN exec $SHELL

RUN git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
RUN exec $SHELL

RUN rbenv install 2.1.2
RUN rbenv global 2.1.2

RUN add-apt-repository ppa:chris-lea/node.js
RUN apt-get update
RUN apt-get install nodejs

RUN npm install -g bower

RUN mkdir /data

WORKDIR /data

EXPOSE 3000

CMD ["bundle exec rails s"]

