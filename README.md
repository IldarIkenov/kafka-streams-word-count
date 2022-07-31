# kafka-streams-word-count

## Requirements
Docker: We will use it to start Kafka and create the topics
Java 17
An IDE like Intellij IDEA

```
docker compose -f ./docker-compose.yml up
```
or
```
docker-compose up
```
## Publishing a message and consuming the results
1 terminal for the consumer
```
docker exec -it kafka /bin/bash
```
insert command [appuser@kafka ~]$ 
```
kafka-console-consumer --topic word-count --bootstrap-server localhost:9092 \
 --from-beginning \
 --property print.key=true \
 --property key.separator=" : " \
 --key-deserializer "org.apache.kafka.common.serialization.StringDeserializer" \
 --value-deserializer "org.apache.kafka.common.serialization.LongDeserializer"
 ```
 insert any text 
 ```
>Hello kafka streams
>Hello world
```
 2 new terminal for the produser
 ```
 docker exec -it kafka /bin/bash
 ```
 insert command [appuser@kafka ~]$
 ```
 kafka-console-producer --topic sentences --bootstrap-server localhost:9092
 ```

result
```
hello : 1
kafka : 1
streams : 1
hello : 2
world : 1
```
