Dockerfile for running an [Apache Mesos](http://mesos.apache.org/) slave node.

### Configuration

Mesos allows you to set all [configuration
options](http://mesos.apache.org/documentation/latest/configuration/) via
environment variables.  That means that you don't need any additional scripts to
start up a Mesos slave node using this Docker image; just pass in `-e` options
to set each configuration option:

    $ docker run -d \
        -e MESOS_LOG_DIR=/var/log \
        -e MESOS_MASTER=[zookeeper URL] \
        -p 5051:5051 \
        redjack/mesos-slave

Also note the `-p` option, which exposes the default Mesos slave TCP port
(5051) on the container host.

### Running Docker containerizer

The Docker containerizer can be run via the following options:

    $ docker run -d \
        -e MESOS_LOG_DIR=/var/log \
        -e MESOS_MASTER=[zookeeper URL] \
        -e MESOS_EXECUTOR_REGISTRATION_TIMEOUT=5mins \
        -e MESOS_ISOLATOR=cgroups/cpu,cgroups/mem \
        -e MESOS_CONTAINERIZERS=docker,mesos \
        -v /run/docker.sock:/run/docker.sock \
        -v /sys:/sys \
        -v /proc:/proc \
        -p 5051:5051 \
        redjack/mesos-slave
