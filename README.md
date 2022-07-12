# Configuratin
Make a copy of `src/main/resource/ccloud-java-template.properties` and fill the API-KEY data and Bootstrap server

Create a couple of topics for input and output data

# Running TX Processor
```shell
./gradlew runTxOffsetConsumer -Pconfig=src/main/resources/ccloud-java.properties -Pin=input-topic -Pout=output-topic
```

# Running Standard Processor
```shell
./gradlew runSyncOffsetConsumer -Pconfig=src/main/resources/ccloud-java.properties -Pin=input-topic -Pout=output-topic
```

# Running Check
```shell
kafka-console-consumer --bootstrap-server <bootrap:9092> --consumer.config src/main/resources/ccloud-java.properties --topic output-topic --consumer-property "isolation.level=read_committed" --property print.partition=true --property print.offset=true --property print.key=true
```