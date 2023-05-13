#

# Create Topic
`kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic streams-plaintext-input` 

# Create Topic
`kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic streams-wordcount-output`

# List Topic
`kafka-topics --bootstrap-server localhost:9092 --list`

# Produce Some Data
`kafka-console-producer --bootstrap-server localhost:9092 --topic streams-plaintext-input` 

```
>kafka streams udemy
>kafka data processing
>kafka streams course
>
```
