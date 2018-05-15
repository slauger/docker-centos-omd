FROM centos:latest
MAINTAINER Simon Lauger <simon@lauger.name>

LABEL org.label-schema.url="https://github.com/slauger/docker-centos-omd" \
      org.label-schema.name="mod-gearman-worker"

ENV SERVER="localhost:4730"
ENV KEY="changeit"

RUN yum install -y epel-release && \
    yum upgrade -y && \
    yum clean all && \
    rm -rf /var/cache/yum/*

COPY files/labs-consol-stable.repo /etc/yum.repos.d/labs-consol-stable.repo

RUN yum install -y mod_gearman && \
    yum clean all && \
    rm -rf /var/cache/yum/*

USER naemon

CMD ["/usr/bin/mod_gearman_worker", "--logmode=stdout", "--p1_file=/usr/share/mod_gearman/mod_gearman_p1.pl", "--debug=3", "--debug-result", "--server=${SERVER}", "--key=${KEY}"]
