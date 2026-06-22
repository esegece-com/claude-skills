# TIdReplyFTP

kind: class
unit: IdReplyFTP

## Properties

| Delphi | Type |
| --- | --- |
| `ReplyFormat: TIdReplyRFCFormat` | [TIdReplyRFCFormat](./TIdReplyRFCFormat.md) |
| `FormattedReply: TStrings` | `TStrings` |
| `NumericCode: Integer` | `Integer` |
| `Code: string` | `string` |
| `Text: TStrings` | `TStrings` |

## Methods

```pascal
constructor CreateWithReplyTexts(ACollection: TCollection = nil; AReplyTexts: TIdReplies = nil);
procedure Clear;
procedure RaiseReplyError;
function ReplyExists: Boolean;
procedure SetReply(const ACode: Integer; const AText: string);
procedure UpdateText;
```

