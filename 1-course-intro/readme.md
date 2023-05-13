#

# Create Topic
```kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic streams-plaintext-input```

# Create Topic
```kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic streams-wordcount-output```

# List Topic
```kafka-topics --bootstrap-server localhost:9092 --list```

# Produce Some Data
```kafka-console-producer --bootstrap-server localhost:9092 --topic streams-plaintext-input``` 

```
>kafka streams udemy
>kafka data processing
>kafka streams course
>
```

# Check Data
```
kafka-console-consumer --bootstrap-server localhost:9092 --topic streams-plaintext-input --from-beginning
kafka streams udemy
kafka data processing
kafka streams course
```

# Output and then run the program

```
kafka-console-consumer --bootstrap-server localhost:9092 \
    --topic streams-wordcount-output \
    --from-beginning \
    --formatter kafka.tools.DefaultMessageFormatter \
    --property print.key=true \
    --property print.value=true \
    --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
    --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
kafka	1
streams	1
udemy	1
kafka	2
data	1
processing	1
kafka	3
streams	2
course	1
```

# Run the Program
```
kafka-run-class org.apache.kafka.streams.examples.wordcount.WordCountDemo
```
