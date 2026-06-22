# TOnSiteCHOWN

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; var AOwner, AGroup : String; const AFileName : TIdFTPFileName; var VAUth : Boolean) of object
```

