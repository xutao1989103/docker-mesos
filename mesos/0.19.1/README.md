Dockerfile for [Apache Mesos](http://mesos.apache.org/).  This Dockerfile is a
base image, and isn't intended to be run directly.  It installs Apache Mesos
using the packages built by [Mesosphere](http://mesosphere.io/downloads/).  Use
the [mesos-master](../mesos-master/) or [mesos-slave](../mesos-slave/) images to
run Mesos in master or slave mode, respectively.

This image is tagged to allow you to pin your installations to a specific recent
version of Mesos.  The following versions are available:

  * `0.21.0` (aka `latest`)
  * `0.20.1`
  * `0.20.0`
  * `0.19.1`
