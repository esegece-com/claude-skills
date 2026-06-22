# TsgcWSDeribitSubscribeEvent

kind: event handler type
unit: sgcWebSocket_API_Deribit

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequestId: Integer; aSuccess: Boolean; const aError, aRawMessage: string) of object
```

