# TsgcWebView2DownloadStartingEvent

kind: event handler type
unit: sgcWebView2_Classes

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aURI, aResultFilePath: string; var aCancel: Boolean; var aHandled: Boolean; var aFilePath: string) of object
```

