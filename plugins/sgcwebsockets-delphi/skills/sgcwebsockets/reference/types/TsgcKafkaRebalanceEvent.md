# TsgcKafkaRebalanceEvent

kind: event handler type
unit: sgcKafka_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aGroupId, aMemberId: string; aGenerationId: Integer) of object
```

