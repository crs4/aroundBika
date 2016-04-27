# Based on gmauro/debian-ansible
FROM gmauro/debian-ansible
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN git clone https://github.com/gmauro/boxed-irods /tmp/boxed-irods
WORKDIR /tmp/boxed-irods
RUN ansible-playbook icat.yml

# Add VOLUMEs to allow backup of config, logs and databases
VOLUME ["/etc", "/home", "/var/log", "/var/lib"]

EXPOSE 1247

RUN apt-get update && apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]