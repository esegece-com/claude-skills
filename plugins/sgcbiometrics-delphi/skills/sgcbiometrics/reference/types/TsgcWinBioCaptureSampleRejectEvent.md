# TsgcWinBioCaptureSampleRejectEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSample: WINBIO_BIR; aRejectDetail: WINBIO_REJECT_DETAIL) of object
```

