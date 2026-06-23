FROM confluentinc/cp-server-connect-base:8.2.2

# Kafka Connect S3
RUN curl -L -o /tmp/confluentinc-kafka-connect-s3-12.1.5.zip \
  https://pub-7ea43db0438a4a858ae4acf14c0ae7f2.r2.dev/kafka/libs/confluentinc-kafka-connect-s3-12.1.5.zip \
  && confluent-hub install --no-prompt /tmp/confluentinc-kafka-connect-s3-12.1.5.zip

# Kafka Connect JDBC
RUN curl -L -o /tmp/confluentinc-kafka-connect-jdbc-10.9.4.zip \
  https://pub-7ea43db0438a4a858ae4acf14c0ae7f2.r2.dev/kafka/libs/confluentinc-kafka-connect-jdbc-10.9.4.zip \
  && confluent-hub install --no-prompt /tmp/confluentinc-kafka-connect-jdbc-10.9.4.zip

# Remove archives
RUN rm -f /tmp/*.zip
