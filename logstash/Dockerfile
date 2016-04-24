FROM java:openjdk-8u72-jdk

MAINTAINER itzg

ENV LOGSTASH_VERSION 2.3.0

RUN wget -qO /tmp/logstash.tgz https://download.elastic.co/logstash/logstash/logstash-${LOGSTASH_VERSION}.tar.gz && \
  tar -C /opt -xf /tmp/logstash.tgz && \
  rm /tmp/logstash.tgz

WORKDIR /opt/logstash-${LOGSTASH_VERSION}

# For collectd reception
EXPOSE 25826

# /conf is the default directory where our logstash will read pipeline config files
# /logs is an optional attach point to reference something like /var/log on the host
VOLUME ["/conf","/logs"]

ENV PLUGIN_UPDATES 2016-04-01

RUN bin/logstash-plugin install logstash-input-heartbeat
RUN bin/logstash-plugin install logstash-output-elasticsearch_groom

CMD ["bin/logstash","agent","-f","/conf"]
