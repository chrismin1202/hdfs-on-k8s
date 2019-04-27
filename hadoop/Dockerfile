FROM alpine:3.9

ENV JAVA_HOME /usr/lib/jvm/default-jvm
ENV HADOOP_VERSION 3.2.0
ENV HADOOP_URL https://www.apache.org/dist/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz

ENV HADOOP_HOME=/opt/hadoop-$HADOOP_VERSION
ENV HADOOP_CONF_DIR=/etc/hadoop
ENV MULTIHOMED_NETWORK=1

ENV USER=root
ENV PATH ${JAVA_HOME}/bin:${HADOOP_HOME}/bin/:${PATH}

RUN apk -U update \
    && apk add bash curl openssh-client wget openssl openjdk8-jre supervisor perl \
    && apk upgrade \
    && curl -fSL "$HADOOP_URL" -o /tmp/hadoop.tar.gz \
    && tar -xvf /tmp/hadoop.tar.gz -C /opt/ \
    && rm /tmp/hadoop.tar.gz* \
    && ln -s $HADOOP_HOME/etc/hadoop /etc/hadoop \
    && mkdir $HADOOP_HOME/logs \
    && mkdir /hadoop-data \
    && rm -Rf $HADOOP_HOME/share/doc/hadoop

ADD entrypoint.sh /entrypoint.sh
RUN chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
