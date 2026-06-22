# TCallbackExEvent

kind: event handler type
unit: IdSSLOpenSSL

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; const AsslSocket: PSSL; const AWhere, Aret: TIdC_INT; const AType, AMsg: String) of object
```

