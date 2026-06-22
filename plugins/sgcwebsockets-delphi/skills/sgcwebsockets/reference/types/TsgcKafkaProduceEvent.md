# TsgcKafkaProduceEvent

kind: event handler type
unit: sgcKafka_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aTopic: string; aPartition: Integer; aOffset: Int64; aErrorCode: SmallInt) of object
```

