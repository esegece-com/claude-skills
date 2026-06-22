# TReceiveErrorEvent

kind: event handler type
unit: IdHL7

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; AConnection: TIdTCPConnection; AMsg: String; AException: Exception; var VReply: String; var VDropConnection: Boolean) of object
```

