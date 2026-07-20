FROM debian:trixie

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    tar \
    default-jdk \
    dnsutils \
    iputils-ping \
    netcat-openbsd \
 && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/kafka && \
    curl -L -o /tmp/kafka.tgz \
      https://downloads.apache.org/kafka/4.3.1/kafka_2.13-4.3.1.tgz && \
    tar -xzf /tmp/kafka.tgz -C /opt/kafka --strip-components=1 && \
    rm /tmp/kafka.tgz

ENV PATH="/opt/kafka/bin:${PATH}"

CMD ["/bin/bash"]
