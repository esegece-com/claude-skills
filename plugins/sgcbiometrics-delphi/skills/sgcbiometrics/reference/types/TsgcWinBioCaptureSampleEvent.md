# TsgcWinBioCaptureSampleEvent

kind: event handler type
unit: sgcBiometrics_WinBio_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSample: WINBIO_BIR; const aHeader: WINBIO_BIR_HEADER; const aAnsiBdbHeader: WINBIO_BDB_ANSI_381_HEADER; const aAnsiBdbRecord: WINBIO_BDB_ANSI_381_RECORD; const aFirstPixel: PBYTE) of object
```

