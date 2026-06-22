# TsgcOnSSLVerifyPeer

kind: event handler type
unit: sgcSocket_Classes_Indy

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Certificate: TIdX509; AOk: Boolean; ADepth, AError: Integer; var Accept: Boolean) of object
```

