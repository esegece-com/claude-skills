# TsgcWinBioIdentifyEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aUnitId: Integer; const aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE; const aRejectDetail: WINBIO_REJECT_DETAIL) of object
```

