FROM debian:jessie
MAINTAINER Ben Wilson

RUN apt-get update && apt-get install -y \
  curl gcc libc6-dev make libssl-dev zlib1g-dev e2fslibs-dev && \
  apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV TARSNAP_VERSION 1.0.37

RUN curl https://www.tarsnap.com/tarsnap-signing-key-2016.asc \
  -o /tmp/tarsnap-signing-key-2016.asc

RUN gpg --import /tmp/tarsnap-signing-key-2016.asc

RUN mkdir -p /usr/src/tarsnap 
WORKDIR /usr/src/tarsnap
RUN curl https://www.tarsnap.com/download/tarsnap-autoconf-$TARSNAP_VERSION.tgz \
  -o /usr/src/tarsnap/tarsnap-autoconf-$TARSNAP_VERSION.tgz

RUN curl https://www.tarsnap.com/download/tarsnap-sigs-$TARSNAP_VERSION.tgz.asc \
  -o /usr/src/tarsnap/tarsnap-sigs-$TARSNAP_VERSION.tgz.asc

RUN tar -xzf tarsnap-autoconf-$TARSNAP_VERSION.tgz \
  && cd tarsnap-autoconf-$TARSNAP_VERSION \
  && ./configure \
  && make all

