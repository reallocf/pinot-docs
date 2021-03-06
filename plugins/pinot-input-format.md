# Pinot Input Format

Pinot Input format is a set of plugins with the goal of reading data from files during data ingestion. It can be split into two additional types: record encoders \(for batch jobs\) and decoders \(for ingestion\).  

Currently supported Pinot Input Formats:

* Batch
  * Avro
  * CSV
  * JSON
  * ORC
  * PARQUET
  * THRIFT
* Streaming
  * Avro
  * Avro Confluent
    * To use the avro confluent stream decoder, the realtime table configuration should point to the `streamConfigs` section of `tableIndexConfig` should point to the avro confluent stream decoder. Here is an example configuration:

```text
"streamConfigs": {
  "streamType": "kafka",
  "stream.kafka.consumer.type": "LowLevel",
  "stream.kafka.topic.name": "kafka-topic",
  "stream.kafka.decoder.class.name": "org.apache.pinot.plugin.inputformat.avro.confluent.KafkaConfluentSchemaRegistryAvroMessageDecoder",
  "stream.kafka.consumer.factory.class.name": "org.apache.pinot.plugin.stream.kafka20.KafkaConsumerFactory",
  "stream.kafka.decoder.prop.schema.registry.rest.url": "http://<schema registry host>:8081",
  "stream.kafka.zk.broker.url": "<zk broker url>/",
  "stream.kafka.broker.list": "<kafka broker url>",
  "realtime.segment.flush.threshold.time": "24h",
  "realtime.segment.flush.threshold.size": "0",
  "realtime.segment.flush.desired.size": "150M",
  "stream.kafka.consumer.prop.auto.isolation.level": "read_committed",
  "stream.kafka.consumer.prop.auto.offset.reset": "smallest",
  "stream.kafka.consumer.prop.group.id": "<group id>",
  "stream.kafka.consumer.prop.client.id": "<client id>"
}
```

 

* JSON



