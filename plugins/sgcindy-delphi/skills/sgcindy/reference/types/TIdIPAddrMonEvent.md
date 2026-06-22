# TIdIPAddrMonEvent

kind: event handler type
unit: IdIPAddrMon

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; AAdapter: Integer; AOldIP, ANewIP: string) of object
```

