FROM  gmauro/ansible:2.6_ubuntu16.04
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /tmp

RUN git clone https://github.com/gmauro/ansible-bika.webservice && \
    cd ansible-bika.webservice && \
    ansible-playbook -i localhost, local.yml -e "@defaults/main.yml"


RUN apt-get update && \
    apt-get install -y supervisor && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ADD supervisord.conf /etc/supervisor/supervisord.conf

EXPOSE 8088
EXPOSE 8086

USER bika
WORKDIR /home/bika
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]