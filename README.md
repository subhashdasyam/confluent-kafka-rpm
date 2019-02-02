# confluent-kafka-rpm
Confluent Kafka RPM based docker images


# cp-zookeper

#### Build the zookeeper image with cp-zookeeper as its name and run below command.

```
docker run -d \
--net=host \
--name=zookeeper \
-e ZOOKEEPER_CLIENT_PORT=32181 \
-e ZOOKEEPER_TICK_TIME=2000 \
-e ZOOKEEPER_SYNC_LIMIT=2 \
cp-zookeeper
```

# cp-kafka

#### Build the kafka image with cp-kafka as its name and run below command.

```
docker run -d \
    --net=host \
    --name=kafka \
    -e KAFKA_ZOOKEEPER_CONNECT=localhost:32181 \
    -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:29092 \
    -e KAFKA_BROKER_ID=2 \
    -e KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1 \
    cp-kafka
```

# cp-schema-registry

#### Build the schema registry image with cp-schema-registry as its name and run below command.

```
docker run -d \
  --net=host \
  --name=schema-registry \
  -e SCHEMA_REGISTRY_KAFKASTORE_CONNECTION_URL=localhost:32181 \
  -e SCHEMA_REGISTRY_HOST_NAME=localhost \
  -e SCHEMA_REGISTRY_LISTENERS=http://localhost:8081 \
  -e SCHEMA_REGISTRY_DEBUG=true \
  cp-schema-registry
  ```
  
  # cp-kafka-connect
  
  #### Build kafka-connect-base image first then 
  #### Build the cp-kafka-connect image with cp-kafka-connect as its name and run below command.

  ```
  docker run -d \
  --name=kafka-connect \
  --net=host \
  -e CONNECT_BOOTSTRAP_SERVERS=localhost:29092 \
  -e CONNECT_REST_PORT=28082 \
  -e CONNECT_GROUP_ID="quickstart" \
  -e CONNECT_CONFIG_STORAGE_TOPIC="quickstart-config" \
  -e CONNECT_OFFSET_STORAGE_TOPIC="quickstart-offsets" \
  -e CONNECT_STATUS_STORAGE_TOPIC="quickstart-status" \
  -e CONNECT_KEY_CONVERTER="org.apache.kafka.connect.json.JsonConverter" \
  -e CONNECT_VALUE_CONVERTER="org.apache.kafka.connect.json.JsonConverter" \
  -e CONNECT_INTERNAL_KEY_CONVERTER="org.apache.kafka.connect.json.JsonConverter" \
  -e CONNECT_INTERNAL_VALUE_CONVERTER="org.apache.kafka.connect.json.JsonConverter" \
  -e CONNECT_REST_ADVERTISED_HOST_NAME="localhost" \
  -e CONNECT_PLUGIN_PATH=/usr/share/java \
  cp-kafka-connect
  ```
