# TsgcWebView2ContextMenuRequestedEvent

kind: event handler type
unit: sgcWebView2_Classes

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aMenuItems: string; aContextKind: Integer; const aLocation: TPoint; var aHandled: Boolean) of object
```

