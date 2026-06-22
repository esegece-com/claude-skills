# TIdOnSelectAuthorization

kind: event handler type
unit: IdHTTP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; var AuthenticationClass: TIdAuthenticationClass; AuthInfo: TIdHeaderList) of object
```

