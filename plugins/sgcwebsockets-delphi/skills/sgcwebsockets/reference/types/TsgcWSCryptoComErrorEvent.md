# TsgcWSCryptoComErrorEvent

kind: event handler type
unit: sgcWebSocket_API_CryptoCom

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aErrorCode: Integer; const aErrorMessage: string; const aRawMessage: string) of object
```

