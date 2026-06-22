# TIdCommandHandler

kind: class
unit: IdCommandHandlers

## Properties

| Delphi | Type |
| --- | --- |
| `DataObject: TObject` | `TObject` |
| `DataValue: PtrInt` | `PtrInt` |
| `Data: TObject` | `TObject` |
| `CmdDelimiter: Char` | `Char` |
| `Command: string` | `string` |
| `Description: TStrings` | `TStrings` |
| `Disconnect: boolean` | `boolean` |
| `Enabled: boolean` | `boolean` |
| `ExceptionReply: TIdReply` | `TIdReply` |
| `Name: string` | `string` |
| `NormalReply: TIdReply` | `TIdReply` |
| `ParamDelimiter: Char` | `Char` |
| `ParseParams: Boolean` | `Boolean` |
| `Response: TStrings` | `TStrings` |
| `Tag: Integer` | `Integer` |
| `HelpSuperScript: String` | `String` |
| `HelpVisible: Boolean` | `Boolean` |

## Events

| Delphi | Type |
| --- | --- |
| `OnCommand: TIdCommandEvent` | `TIdCommandEvent` |

## Methods

```pascal
function Check(const AData: string; AContext: TIdContext): boolean;
procedure DoCommand(const AData: string; AContext: TIdContext; AUnparsedParams: string);
procedure DoParseParams(AUnparsedParams: string; AParams: TStrings);
function NameIs(const ACommand: string): Boolean;
```

