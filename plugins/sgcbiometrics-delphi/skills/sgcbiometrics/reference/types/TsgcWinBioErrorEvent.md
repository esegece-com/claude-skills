# TsgcWinBioErrorEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aError: String; const aCode: Integer = 0) of object
```

