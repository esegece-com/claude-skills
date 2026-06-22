# TIdHTTPOnRedirectEvent

kind: event handler type
unit: IdHTTP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; var dest: string; var NumRedirect: Integer; var Handled: boolean; var VMethod: TIdHTTPMethod) of object
```

