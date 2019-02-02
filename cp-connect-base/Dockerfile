FROM cp-kafka
EXPOSE 8083
ENV COMPONENT=kafka-connect
RUN yum install -y confluent-schema-registry.noarch confluent-control-center.noarch confluent-hub-client.noarch \
    && rm -rf /tmp/* \
    && yum clean all \
    && mkdir -p /etc/${COMPONENT} /etc/${COMPONENT}/secrets /etc/${COMPONENT}/jars \
    && chmod -R ag+w /etc/${COMPONENT} /etc/${COMPONENT}/secrets /etc/${COMPONENT}/jars
VOLUME ["/etc/${COMPONENT}/jars", "/etc/${COMPONENT}/secrets"]
COPY confluent/docker /etc/confluent/docker
CMD ["/etc/confluent/docker/run"]
