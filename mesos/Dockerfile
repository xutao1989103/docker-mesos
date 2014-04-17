FROM ubuntu
MAINTAINER RedJack, LLC

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update

WORKDIR /tmp
RUN \
  apt-get install -y curl && \
  curl -O http://s3.amazonaws.com/downloads.mesosphere.io/master/ubuntu/12.04/mesos_0.18.0_amd64.deb && \
  dpkg --unpack mesos_0.18.0_amd64.deb && \
  apt-get install -f -y && \
  rm mesos_0.18.0_amd64.deb && \
  apt-get clean
