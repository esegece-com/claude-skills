# TsgcWinBioEnrollCommitEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aIdentity: WINBIO_IDENTITY; aIsNewTemplate: Boolean) of object
```

