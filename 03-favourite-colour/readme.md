

kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic favourite-colour-input

kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic user-keys-and-colours --config cleanup.policy=compact

kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic favourite-colour-output --config cleanup.policy=compact


# launch a Kafka consumer
```shell
kafka-console-consumer --bootstrap-server localhost:9092 \
    --topic favourite-colour-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
```

Output

```shell
kafka-console-producer --bootstrap-server localhost:9092 --topic favourite-colour-input
>prateek,blue
>john,green
>prateek,red
>alice,red
>

kafka-console-consumer --bootstrap-server localhost:9092 \
    --topic favourite-colour-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
blue	1
green	1
blue	0
red	1
red	2
```