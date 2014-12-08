FROM ubuntu
MAINTAINER RedJack, LLC

ENV DEBIAN_FRONTEND noninteractive
ENV MESOS_VERSION 0.19.1
ENV MESOS_PKG_RELEASE 1.0

RUN apt-get update

# Make sure to install OpenJDK 6 explicitly.  The libmesos library includes an
# RPATH entry, which is needed to find libjvm.so at runtime.  This RPATH is
# hard-coded to the OpenJDK version that was present when the package was
# compiled.  So even though the Debian package claims that it works with either
# OpenJDK 6 or OpenJDK 7, the fact that Mesosphere compiled with OpenJDK 6 means
# that we have to have that specific version present at runtime.

WORKDIR /tmp
RUN \
  apt-get install -y curl openjdk-6-jre-headless docker.io && \
  curl -s -O https://downloads.mesosphere.io/master/ubuntu/14.04/mesos_${MESOS_VERSION}-${MESOS_PKG_RELEASE}.ubuntu1404_amd64.deb && \
  dpkg --unpack mesos_${MESOS_VERSION}-${MESOS_PKG_RELEASE}.ubuntu1404_amd64.deb && \
  apt-get install -f -y && \
  rm mesos_${MESOS_VERSION}-${MESOS_PKG_RELEASE}.ubuntu1404_amd64.deb && \
  apt-get clean
