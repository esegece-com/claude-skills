# TIdMappedTelnetCheckHostPort

kind: event handler type
unit: IdMappedTelnet

A handler assigned to this event must match this signature:

```pascal
procedure (AContext: TIdMappedPortContext; const AHostPort: String; var VHost, VPort: String) of object
```

