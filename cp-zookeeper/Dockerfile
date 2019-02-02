FROM cp-base
EXPOSE 2181 2888 3888
ENV COMPONENT=zookeeper

RUN yum install -y confluent-kafka-2.11.noarch \
    && rm -rf /tmp/* \
    && yum clean all \
    && mkdir -p /var/lib/${COMPONENT}/data /var/lib/${COMPONENT}/log /etc/${COMPONENT}/secrets \
    && chmod -R ag+w /etc/kafka /var/lib/${COMPONENT}/data /etc/${COMPONENT}/secrets /var/lib/${COMPONENT}/log

VOLUME ["/var/lib/${COMPONENT}/data", "/etc/${COMPONENT}/secrets", "/var/lib/${COMPONENT}/log"]
COPY confluent/docker /etc/confluent/docker
CMD ["/etc/confluent/docker/run"]
