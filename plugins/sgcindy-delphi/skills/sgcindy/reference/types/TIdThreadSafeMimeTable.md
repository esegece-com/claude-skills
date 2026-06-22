# TIdThreadSafeMimeTable

kind: class
unit: IdCustomHTTPServer

## Properties

| Delphi | Type |
| --- | --- |
| `LoadTypesFromOS: Boolean` | `Boolean` |

## Events

| Delphi | Type |
| --- | --- |
| `OnBuildCache: TNotifyEvent` | `TNotifyEvent` |

## Methods

```pascal
procedure BuildCache;
procedure AddMimeType(const Ext, MIMEType: string; const ARaiseOnError: Boolean = True);
function GetFileMIMEType(const AFileName: string): string;
function GetDefaultFileExt(const MIMEType: string): string;
procedure LoadFromStrings(const AStrings: TStrings; const MimeSeparator: Char = '=');
procedure SaveToStrings(const AStrings: TStrings; const MimeSeparator: Char = '=');
function Lock: TIdMimeTable;
procedure Unlock;
```

