# TsgcWSMetaDataEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Dataset_Message

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const JSON: IsgcObjectJSON) of object
```

