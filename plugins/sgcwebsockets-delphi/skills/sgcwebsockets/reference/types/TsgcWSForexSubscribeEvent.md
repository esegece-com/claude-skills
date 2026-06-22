# TsgcWSForexSubscribeEvent

kind: event handler type
unit: sgcWebSocket_API_Forex

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aAdapter: string; const aGroup: string; const aItems: Integer; const aFields: Integer) of object
```

