FROM centos
MAINTAINER Roman Vynar <roman.vynar@percona.com>

EXPOSE 9100 9104

WORKDIR /opt
RUN yum -y install git make python-setuptools
RUN easy_install supervisor
RUN git clone https://github.com/prometheus/node_exporter.git
RUN cd node_exporter && make
RUN git clone https://github.com/prometheus/mysqld_exporter.git
RUN cd mysqld_exporter && make
ADD supervisord.conf /etc/

CMD ["supervisord", "-c", "/etc/supervisord.conf"]
