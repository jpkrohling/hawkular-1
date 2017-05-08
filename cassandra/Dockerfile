FROM jboss/base-jdk:8
MAINTAINER Juraci Paixão Kröhling <jpkroehling+docker@redhat.com>

# Cassandra exposed ports: CQL, thrift, tcp, ssl, jmx
EXPOSE 9042 9160 7000 7001 7199

# Become the root user to be able to install and setup Cassandra under /opt
USER root

# no GPG check: BZ 1445182
RUN yum-config-manager --add-repo https://copr-be.cloud.fedoraproject.org/results/jpkroehling/cassandra/epel-7-x86_64/ && \
    yum install -y bind-utils hawkular-cassandra --nogpgcheck && \
    yum clean all

ADD files /opt/apache-cassandra-3.0.12/
RUN chmod a+rw -R /opt/apache-cassandra-3.0.12

CMD ["/opt/apache-cassandra-3.0.12/bin/run.sh"]
