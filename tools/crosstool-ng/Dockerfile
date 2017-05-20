FROM alpine:3.5

LABEL maintainer "kaendfinger@gmail.com"

RUN apk update && apk add git autoconf automake build-base \
  gperf bison flex texinfo libtool ncurses-dev wget gawk \
  libc-dev help2man sed unzip xz && rm -rf /var/cache/apk/*

RUN cd /root && \
  git clone https://github.com/crosstool-ng/crosstool-ng.git crosstool-ng && \
  cd crosstool-ng && ./bootstrap && ./configure && make && make install && \
  cd .. && rm -rf crosstool-ng && mkdir -p /data/build

RUN mkdir /home/ctng && \
  addgroup -g 1001 ctng && \
  adduser -u 1001 -G ctng -h /home/ctng -s /bin/sh -D ctng && \
  chown -R ctng:ctng /data

VOLUME /data
WORKDIR /data/build

ENTRYPOINT ["ct-ng"]
