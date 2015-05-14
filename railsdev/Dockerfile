FROM phusion/passenger-customizable:latest
MAINTAINER Hemslo <hemslo.wang@gmail.com>

RUN /pd_build/ruby2.2.sh
RUN apt-get update && apt-get install -y \
    libicu-dev \
    cmake \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
