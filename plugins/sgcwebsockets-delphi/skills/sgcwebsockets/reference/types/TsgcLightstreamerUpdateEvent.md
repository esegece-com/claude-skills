# TsgcLightstreamerUpdateEvent

kind: event handler type
unit: sgcLightstreamer

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSubscription: TsgcLightstreamerSubscription; const aItemIndex: Integer; const aFields: TsgcLightstreamerStringArray) of object
```

