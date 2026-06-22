# TsgcWinBioEnumBiometricUnitEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aUnit: WINBIO_UNIT_SCHEMA; const aNum, aCount: Integer) of object
```

