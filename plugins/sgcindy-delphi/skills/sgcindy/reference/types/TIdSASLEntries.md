# TIdSASLEntries

kind: class
unit: IdSASLCollection

## Properties

| Delphi | Type |
| --- | --- |
| `Items[Index[Index: Integer]: TIdSASLListEntry` | [TIdSASLListEntry](./TIdSASLListEntry.md) |
| `OwnerComponent: TComponent (read-only)` | `TComponent` |

## Methods

```pascal
function Add: TIdSASLListEntry;
procedure LoginSASL(const ACmd, AHost, AProtocolName: String; const AOkReplies, AContinueReplies: array of string; AClient : TIdTCPConnection; ACapaReply : TStrings; const AAuthString : String = 'AUTH'; ACanAttemptIR: Boolean = True);
function ParseCapaReply(ACapaReply: TStrings; const AAuthString: String = 'AUTH') : TStrings;
procedure ParseCapaReplyToList(ACapaReply, ADestList: TStrings; const AAuthString: String = 'AUTH');
function FindSASL(const AServiceName: String): TIdSASL;
function Insert(Index: Integer): TIdSASLListEntry;
procedure RemoveByComp(AComponent : TComponent);
function IndexOfComp(AItem : TIdSASL): Integer;
```

