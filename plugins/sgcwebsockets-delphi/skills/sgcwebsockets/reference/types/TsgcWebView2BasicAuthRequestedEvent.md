# TsgcWebView2BasicAuthRequestedEvent

kind: event handler type
unit: sgcWebView2_Classes

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aURI: string; var aUserName, aPassword: string; var aHandled: Boolean) of object
```

