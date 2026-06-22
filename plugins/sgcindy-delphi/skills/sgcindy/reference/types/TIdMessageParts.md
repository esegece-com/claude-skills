# TIdMessageParts

kind: class
unit: IdMessageParts

## Properties

| Delphi | Type |
| --- | --- |
| `AttachmentCount: integer (read-only)` | `integer` |
| `AttachmentEncoding: string` | `string` |
| `Items[Index[Index: Integer]: TIdMessagePart` | [TIdMessagePart](./TIdMessagePart.md) |
| `MessageEncoderInfo: TObject (read-only)` | `TObject` |
| `OwnerMessage: TPersistent (read-only)` | `TPersistent` |
| `RelatedPartCount: integer (read-only)` | `integer` |
| `TextPartCount: integer (read-only)` | `integer` |

## Methods

```pascal
function Add: TIdMessagePart;
procedure CountParts;
```

