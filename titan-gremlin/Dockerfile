FROM java:openjdk-8u72-jdk

MAINTAINER itzg

ENV TITAN_VERSION 0.5.4
ENV TITAN_HADOOP_VER 1

RUN wget -q -O /tmp/titan.zip http://s3.thinkaurelius.com/downloads/titan/titan-$TITAN_VERSION-hadoop${TITAN_HADOOP_VER}.zip
RUN unzip -q /tmp/titan.zip -d /opt && rm /tmp/titan.zip

ENV TITAN_HOME /opt/titan-$TITAN_VERSION-hadoop${TITAN_HADOOP_VER}
WORKDIR $TITAN_HOME

VOLUME ["/conf","/data"]
ADD start-gremlin.sh /opt/start-gremlin.sh

ENV ES_CLUSTER elasticsearch

CMD ["/opt/start-gremlin.sh"]
