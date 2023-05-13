#

```shell
kafka-topics --create --bootstrap-server localhost:9092 --topic word-count-input --replication-factor 1 --partitions 2

kafka-topics --create --bootstrap-server localhost:9092 --topic word-count-output --replication-factor 1 --partitions 2

kafka-console-consumer --bootstrap-server localhost:9092 \ 
    --topic word-count-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
    
kafka-console-producer --bootstrap-server localhost:9092 --topic word-count-input    
```

# With Data

```shell
kafka-console-producer --bootstrap-server localhost:9092 --topic word-count-input
>hello kafka streams
>kafka streams is working
>hello Prateek Kafka
>


kafka-console-consumer --bootstrap-server localhost:9092 \ 
    --topic word-count-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
streams	2
is	1
kafka	3
working	1
hello	2
prateek	1
```