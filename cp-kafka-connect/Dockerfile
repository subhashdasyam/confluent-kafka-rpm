FROM cp-connect-base
ENV COMPONENT=kafka-connect
RUN yum update -y && yum install -y confluent-kafka-connect-* \
    && rm -rf /tmp/* \
    && yum clean all \
    && confluent-hub install confluentinc/kafka-connect-gcs:latest --no-prompt
