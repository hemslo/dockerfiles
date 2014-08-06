RUN git clone https://github.com/sstephenson/ruby-build.git /root/ruby-build
RUN cd /root/ruby-build && ./install.sh
RUN ruby-build 2.1.2 /usr/local
RUN gem install bundler

RUN npm install -g bower

RUN mkdir -p /data/website
