# TsgcWSBeforeRecordEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Dataset_Message

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const Dataset: TDataset; const JSON: IsgcObjectJSON; var Handled: Boolean) of object
```

