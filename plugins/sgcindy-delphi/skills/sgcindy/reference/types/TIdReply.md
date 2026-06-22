# TIdReply

kind: class
unit: IdReply

## Properties

| Delphi | Type |
| --- | --- |
| `FormattedReply: TStrings` | `TStrings` |
| `NumericCode: Integer` | `Integer` |
| `Code: string` | `string` |
| `Text: TStrings` | `TStrings` |

## Methods

```pascal
procedure Clear;
constructor CreateWithReplyTexts(ACollection: TCollection; AReplyTexts: TIdReplies);
procedure RaiseReplyError;
function ReplyExists: Boolean;
procedure SetReply(const ACode: Integer; const AText: string);
procedure UpdateText;
```

