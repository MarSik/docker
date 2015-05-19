FROM fedora:20
MAINTAINER Martin Sivak <msivak@redhat.com>

RUN yum -y install http://resources.ovirt.org/pub/yum-repo/ovirt-release35.rpm
RUN yum -y install http://resources.ovirt.org/pub/yum-repo/ovirt-release35-snapshot.rpm

RUN yum -y install http://jenkins.ovirt.org/job/ovirt-optimizer_master_create-rpms_gerrit/221/artifact/exported-artifacts/ovirt-optimizer-0.9-0.85.201505191327.fc20.noarch.rpm http://jenkins.ovirt.org/job/ovirt-optimizer_master_create-rpms_gerrit/221/artifact/exported-artifacts/ovirt-optimizer-dependencies-0.9-0.85.201505191327.fc20.noarch.rpm http://jenkins.ovirt.org/job/ovirt-optimizer_master_create-rpms_gerrit/221/artifact/exported-artifacts/ovirt-optimizer-jetty-0.9-0.85.201505191327.fc20.noarch.rpm
RUN /usr/bin/ovirt-optimizer-setup

# Setup ovirt engine REST address
RUN sed -i -e 's/localhost/10.34.61.26/' /etc/ovirt-optimizer/ovirt-optimizer.properties

EXPOSE 8080
ENTRYPOINT exec /usr/share/jetty/bin/jetty.sh

