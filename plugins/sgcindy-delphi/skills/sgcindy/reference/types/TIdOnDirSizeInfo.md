# TIdOnDirSizeInfo

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender : TIdFTPServerContext; const APathName : TIdFTPFileName; var VIsAFile : Boolean; var VSpace : Int64) of object
```

