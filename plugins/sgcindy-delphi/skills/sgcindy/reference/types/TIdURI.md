# TIdURI

kind: class
unit: IdURI

## Properties

| Delphi | Type |
| --- | --- |
| `Bookmark: string` | `string` |
| `Document: string` | `string` |
| `Host: string` | `string` |
| `Password: string` | `string` |
| `Path: string` | `string` |
| `Params: string` | `string` |
| `Port: string` | `string` |
| `Protocol: string` | `string` |
| `URI: string` | `string` |
| `Username: string` | `string` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](./TIdIPVersion.md) |

## Methods

```pascal
function GetFullURI(const AOptionalFields: TIdURIOptionalFieldsSet = [ofAuthInfo, ofBookmark]): String;
function GetPathAndParams: String;
```

