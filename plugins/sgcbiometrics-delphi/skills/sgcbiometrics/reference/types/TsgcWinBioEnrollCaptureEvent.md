# TsgcWinBioEnrollCaptureEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aSwipes: Integer; const aResult: WINBIO_ENROLL_RESULT; const aRejectDetail: WINBIO_REJECT_DETAIL) of object
```

