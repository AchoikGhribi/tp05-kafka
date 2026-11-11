# TP05: Real-Time Data Streaming with Apache Kafka

**University of Eloued - Big Data Analytics**
**GHRIBI ACHOIK - Groupe 1**

---

## Project Structure
```
tp05-kafka/
├── compose.yaml
├── requirements.txt
├── producer.py
├── consumer.py
├── README.md
└── screenshots/
```


---

## Setup Instructions

1. Start Kafka:
```bash
docker compose up -d

2.Install Python dependencies:

pip install -r requirements.txt

3.Run Consumer first:

python consumer.py

4.Run Producer:

python producer.py

## Answers to Questions ##

Q1: What problem does Apache Kafka solve in a data-streaming architecture?
Kafka acts as a distributed event streaming platform. It decouples data producers from consumers, allowing multiple applications to consume the same real-time stream without delays. It provides high throughput, fault tolerance, and scalability compared to writing data to static files.


Q2: Define producer, consumer, broker, topic, partition, offset, and consumer group.
#Producer: Application that publishes messages to a topic.

#Consumer: Application that subscribes to a topic and reads messages.

#Broker: A Kafka server that stores and serves messages.

#Topic: A named category/feed where messages are published.

#Partition: A physical subset of a topic; messages are ordered within it.

#Offset: A unique sequential ID for each message within a partition.

#Consumer Group: A set of consumers that cooperatively consume a topic.



 Q3:Quelle est la différence entre un topic Kafka et une partition ?

A topic is a logical category (e.g., campus-sensors). A partition is a physical subdivision of a topic. A topic can have multiple partitions for parallelism. Each partition is an ordered, immutable log.


Q4:Why does the consumer use auto_offset_reset='earliest'? When does this setting apply?

It tells Kafka to start reading from the very first message when the consumer group has no committed offset (e.g., first time running). It applies only when no previous offset exists for the group.


Q5: What is the purpose of the consumer group ID? What happens if a new group ID is used?
The group ID identifies a set of consumers that coordinate to consume a topic. Kafka uses it to assign partitions and track offsets. A new group ID starts fresh, applying auto_offset_reset and reading from the beginning.


Q6: Why is JSON a suitable format for this exercise? Give one limitation.
JSON is human-readable, easy to parse in Python (json.loads), and self-describing. It is ideal for simple sensor events. Limitation: JSON is verbose and less efficient than binary formats (Avro, Protobuf) at scale.


Q7: Explain how Docker Compose simplifies deployment compared with starting services manually.
Docker Compose defines the entire environment (services, networks, volumes) in a single compose.yaml file. One command (docker compose up -d) starts everything. Manually, you'd need many docker run flags and manual network setup—error-prone and hard to reproduce.


Q8: What are the limitations of this single-broker educational setup compared with a production Kafka cluster?

#No replication (no fault tolerance).

#No high availability.

#Limited throughput.

#No ZooKeeper/KRaft quorum.

#No monitoring (Prometheus, Grafana).

#No security (TLS, SASL, ACLs).


Q9: Attach evidence showing the running container, topic description, producer output, and consumer output.
(see screenshots/ folder)

### Problems Encountered and Solutions: ###

1/ ModuleNotFoundError with kafka-python on Python 3.14: Solved by upgrading the library to the latest version.
2/ Consumer could not connect to Kafka: Caused by Docker Desktop being closed; fixed by restarting Docker Desktop.
3/ DeprecationWarning: Non-blocking warning; code works correctly.

Cleanup:
docker compose down

To remove Kafka data:
docker compose down -v




