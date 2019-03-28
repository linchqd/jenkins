FROM jenkins/jnlp-slave:latest

LABEL maintainer="linchqd<13435600095@163.com>"

USER root

COPY maven /usr/share/maven/

RUN chmod +x /usr/share/maven/bin/mvn && ln -s /usr/share/maven/bin/mvn /usr/local/bin/mvn

COPY kubectl /usr/local/bin/

RUN chmod +x /usr/local/bin/kubectl

ENV CERT_DIR /etc/kubernetes/certs

RUN mkdir -p ${CERT_DIR} \
	&& mkdir -p ${CERT_DIR} \
	&& touch ${CERT_DIR}/ca.pem \
	&& touch ${CERT_DIR}/admin.pem \
	&& touch ${CERT_DIR}/admin.key \
	&& mkdir -p /root/.kube
COPY config /root/.kube/

COPY pip.conf /etc/

ENV KUBECONFIG /root/.kube/config

ARG DOCKER_SOCK_DIR=/var/run/docker.sock

COPY docker /usr/bin/

RUN apt-get -y update \
	&& apt-get install -y apt-utils iptables libdevmapper1.02.1 libltdl7 libseccomp2 \
	&& apt-get -y autoremove \
	&& chmod +x /usr/bin/docker \
	&& chmod 600 /root/.kube/config

VOLUME ${CERT_DIR}

VOLUME ${DOCKER_SOCK_DIR}
