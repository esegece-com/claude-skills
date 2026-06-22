# TsgcOnAuth2DeviceCode

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const DeviceCode, UserCode, VerificationURI, VerificationURIComplete : String; const ExpiresIn, Interval: Integer) of object
```

