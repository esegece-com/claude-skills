# TsgcLightstreamerMessageEvent

kind: event handler type
unit: sgcLightstreamer

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSequence: string; const aProg: Integer; const aCommand, aResponse: string; const aCode: Integer) of object
```

