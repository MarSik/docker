FROM centos:7
MAINTAINER Martin Sivak <msivak@redhat.com>

RUN yum -y install http://mirror.oss.maxcdn.com/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
#RUN yum -y install http://resources.ovirt.org/pub/ovirt-master-snapshot-static/rpm/el7/noarch/ovirt-release-master-001-0.9.master.noarch.rpm
RUN yum -y install http://resources.ovirt.org/pub/ovirt-3.6/rpm/el7/noarch/ovirt-release36-002-2.noarch.rpm

ADD *.rpm /root/

RUN yum install -y /root/ovirt-optimizer-0.*.rpm /root/ovirt-optimizer-dependencies-*.rpm /root/ovirt-optimizer-jboss-*.rpm

RUN /usr/bin/ovirt-optimizer-setup

# Setup ovirt engine REST address
RUN sed -i -e 's/localhost/10.34.61.26/' /etc/ovirt-optimizer/ovirt-optimizer.properties

EXPOSE 8080
ENTRYPOINT exec /usr/bin/ovirt-optimizer-jboss

