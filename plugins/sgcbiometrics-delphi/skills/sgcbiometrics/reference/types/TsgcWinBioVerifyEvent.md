# TsgcWinBioVerifyEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE; const aUnitId: Integer; const aMatch: Boolean; const aRejectDetail: WINBIO_REJECT_DETAIL) of object
```

