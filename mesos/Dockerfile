FROM ubuntu
MAINTAINER RedJack, LLC

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get install -y openjdk-6-jre-headless
RUN apt-get install -y libsasl2-2
RUN apt-get install -y python python-boto
RUN apt-get install -y libcurl3-nss

# We do all of the following as one big RUN command so that we don't include the
# (multiple gigabytes) of intermediate build artefacts in the resulting docker
# image.

WORKDIR /tmp
RUN \
  apt-get install -y \
    build-essential libtool autoconf automake \
    openjdk-6-jdk curl libsasl2-dev \
    python-dev libcurl4-nss-dev && \
  curl -O http://download.nextag.com/apache/mesos/0.18.0/mesos-0.18.0.tar.gz && \
  tar xf mesos-0.18.0.tar.gz && \
  mkdir mesos-0.18.0/build && \
  cd mesos-0.18.0/build && \
  ../configure --prefix=/usr && \
  make && \
  make install && \
  make clean && \
  cd /tmp && \
  rm -rf mesos-0.18.0.tar.gz mesos-0.18.0 && \
  apt-get purge -y \
    build-essential libtool autoconf automake \
    openjdk-6-jdk curl libsasl2-dev \
    python-dev libcurl4-nss-dev && \
  apt-get autoremove -y
