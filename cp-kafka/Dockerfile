FROM cp-base
EXPOSE 9092
ENV COMPONENT=kafka
RUN yum install -y confluent-kafka-2.11.noarch 
RUN rm -rf /tmp/* && yum clean all
RUN mkdir -p /var/lib/${COMPONENT}/data /etc/${COMPONENT}/secrets \
    && chmod -R ag+w /etc/kafka /var/lib/${COMPONENT}/data /etc/${COMPONENT}/secrets
VOLUME ["/var/lib/${COMPONENT}/data", "/etc/${COMPONENT}/secrets"]
COPY docker /etc/confluent/docker
CMD ["/etc/confluent/docker/run"]
