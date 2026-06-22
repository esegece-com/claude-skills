# TOnHostCheck

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender:TIdFTPServerContext; const AHost : String; var VAccepted : Boolean) of object
```

