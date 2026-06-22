# TsgcKafkaErrorEvent

kind: event handler type
unit: sgcKafka_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aErrorCode: Integer; const aErrorMessage: string) of object
```

