# TsgcWSPClient_Kafka - Example

Usage of `TsgcWSPClient_Kafka` extracted from the **02.WebSocket_Protocols/13.Kafka** demo. See the full project for context.

API reference: [TsgcWSPClient_Kafka](../reference/api/TsgcWSPClient_Kafka.md)
Source demo: `02.WebSocket_Protocols/13.Kafka` (file `fKafka.pas`)

```pascal
fKafkaProtocol := TsgcWSPClient_Kafka.Create(Self);
fKafkaProtocol.Client := WSClient;
fKafkaProtocol.OnKafkaMessage := OnKafkaMessage;
fKafkaProtocol.OnKafkaError := OnKafkaError;
fKafkaProtocol.OnKafkaConnect := OnKafkaConnect;
fKafkaProtocol.OnKafkaDisconnect := OnKafkaDisconnect;
fKafkaProtocol.OnKafkaProduce := OnKafkaProduce;
```

