# CS3219 OTOT Task D
### A0180340U Rayner Lim Ri Han

#### Link to the GitHub repository: [`https://github.com/rlrh/cs3219-otot-task-d`](https://github.com/rlrh/cs3219-otot-task-d)

#### Instructions:
Requires Docker Engine and Docker Compose.
1. Run:
```
docker-compose up -d
```
2. Test creating a topic for messages:
```
docker exec -it 3-node-kafka-zookeeper-docker_kafka1_1 kafka-topics --zookeeper zookeeper:2181 --create --topic mytopic --partitions 1 --replication-factor 3
```
3. Test the Kafka message consumer using one of the nodes:
```
docker exec -it 3-node-kafka-zookeeper-docker_kafka3_1 kafka-console-consumer --bootstrap-server kafka3:19093 --topic mytopic --from-beginning
```
4. In a different console, test producing some messages on a different node:
```
docker exec -it 3-node-kafka-zookeeper-docker_kafka1_1 kafka-console-producer --broker-list kafka1:19091 --topic mytopic
```
  - The same messages should appear in the Kafka message consumer
