# Kafka Local
## Welcome!

This repository explains the steps to bring up a local kafka instance using docker-compose.

## Prerequisites

To use these files, you must first have the following installed:

- [docker](https://docs.docker.com/engine/installation/)
- [docker-compose](https://docs.docker.com/compose/install/)

## How to use

The following steps will run a local instance of the solution using the configuration file (`docker-compose.yml`):

1. Clone this repository.

```bash
git clone https://github.com/chelosky/kafka-local.git
```

2. Change directory into the root of the project.

```bash
cd  kafka-local
```

3. Build and Run the project with one of the follows commands (with docker-compose commands):

```bash
docker-compose -f docker-compose.yml up --remove-orphans --no-recreate
# if you need the project execute in the background, use the -d, --detach option
docker-compose -f docker-compose.yml up --remove-orphans --no-recreate -d
```

## How to access kafka's bash

```bash
# We locate the container id with docker ps
docker ps
# We enter the command line of the kafka container using its associated id
docker exec -it [CONTAINER_ID] bash
```

## General commands (from kafka container)

| Purpose | Command |
|-----------------------|-------------|
| `Create new topic` | opt/kafka_2.13-2.8.1/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor [NUM_REPLICATION_FACTOR] --partitions [NUM_PARTITIONS] --topic [TOPIC_NAME] |
| `Describe topic` | opt/kafka_2.13-2.8.1/bin/kafka-topics.sh --zookeeper localhost:2181 --topic [TOPIC_NAME] |
| `Delete a topic` | opt/kafka_2.13-2.8.1/bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic [TOPIC_NAME] |
| `Change topic's partitions` | opt/kafka_2.13-2.8.1/bin/kafka-topics.sh --zookeeper localhost:2181 --alter --topic [TOPIC_NAME] --partitions [NEW_NUM_PARTITIONS] |

## Stop Solution

If need to stop the execution of the solution and remove the container associated, then execute one of the follows commands(with docker-compose commands):

```sh
docker-compose down
```

Have a nice day.