# TsgcWinBioDatabaseAddDatabaseEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Storage

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aDatabaseId: WINBIO_UUID; aUnitId: Integer) of object
```

