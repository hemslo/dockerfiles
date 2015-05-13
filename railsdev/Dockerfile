FROM phusion/passenger-customizable:latest
MAINTAINER Hemslo <hemslo.wang@gmail.com>

RUN /pd_build/ruby2.2.sh
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
