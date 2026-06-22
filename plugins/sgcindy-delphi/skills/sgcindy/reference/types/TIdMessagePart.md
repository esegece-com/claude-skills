# TIdMessagePart

kind: class
unit: IdMessageParts

## Properties

| Delphi | Type |
| --- | --- |
| `IsEncoded: Boolean (read-only)` | `Boolean` |
| `MessageParts: TIdMessageParts (read-only)` | `TIdMessageParts` |
| `OwnerMessage: TPersistent (read-only)` | `TPersistent` |
| `Headers: TIdHeaderList (read-only)` | `TIdHeaderList` |
| `CharSet: string` | `string` |
| `ContentDescription: string` | `string` |
| `ContentDisposition: string` | `string` |
| `ContentID: string` | `string` |
| `ContentLocation: string` | `string` |
| `ContentTransfer: string` | `string` |
| `ContentType: string` | `string` |
| `ExtraHeaders: TIdHeaderList` | `TIdHeaderList` |
| `FileName: String` | `String` |
| `Name: String` | `String` |
| `ParentPart: integer` | `integer` |

## Events

| Delphi | Type |
| --- | --- |
| `OnGetMessagePartStream: TOnGetMessagePartStream` | `TOnGetMessagePartStream` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
function GetCharSet(AHeader: string): String;
function ResolveContentType(AContentType: string): string;
```

