This is extension for spotify/kafka


Kafka in Docker
===

This repository provides everything you need to run Kafka in Docker.

Why?
---
The main hurdle of running Kafka in Docker is that it depends on Zookeeper.
Compared to other Kafka docker images, this one runs both Zookeeper and Kafka
in the same container. This means:

* No dependency on an external Zookeeper host, or linking to another container
* Zookeeper and Kafka are configured to work together out of the box

Run
---

```bash
docker run --name kafka \
-p 2181:2181 \
-p 9092:9092 \
--env ADVERTISED_LISTENERS=$(hostname):9092\ 
-d shukla2009/kafka
```

```bash
<KAFKA_HOME>\bin\kafka-console-producer.sh --broker-list $(hostname):9092 --topic test
```

```bash
<KAFKA_HOME>\bin\kafka-console-consumer.sh --zookeeper $(hostname):2181 --topic test
```