FROM cp-base
EXPOSE 8081
ENV COMPONENT=schema-registry
RUN yum install -y confluent-schema-registry.noarch confluent-control-center.noarch confluent-security.noarch \
    && rm -rf /tmp/* && yum clean all \
    && mkdir -p /etc/${COMPONENT}/secrets \
    && chmod -R ag+w /etc/${COMPONENT} /etc/${COMPONENT}/secrets
VOLUME ["/etc/${COMPONENT}/secrets"]
COPY confluent/docker /etc/confluent/docker
CMD ["/etc/confluent/docker/run"]
