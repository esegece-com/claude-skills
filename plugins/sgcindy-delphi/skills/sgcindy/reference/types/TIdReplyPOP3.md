# TIdReplyPOP3

kind: class
unit: IdReplyPOP3

## Properties

| Delphi | Type |
| --- | --- |
| `EnhancedCode: String` | `String` |
| `FormattedReply: TStrings` | `TStrings` |
| `NumericCode: Integer` | `Integer` |
| `Code: string` | `string` |
| `Text: TStrings` | `TStrings` |

## Methods

```pascal
constructor CreateWithReplyTexts( ACollection: TCollection = nil; AReplyTexts: TIdReplies = nil );
procedure Assign(ASource: TPersistent);
procedure Clear;
procedure RaiseReplyError;
function ReplyExists: Boolean;
procedure SetReply(const ACode: Integer; const AText: string);
procedure UpdateText;
```

