# TIdHeaderList

kind: class
unit: IdHeaderList

## Properties

| Delphi | Type |
| --- | --- |
| `Names[Index[Index: Integer]: string (read-only)` | `string` |
| `Values[const[const Name: string]: string` | `string` |
| `Params[const[const Name, Param: string]: string` | `string` |
| `AllParams[const[const Name: string]: string` | `string` |
| `NameValueSeparator: String` | `String` |
| `UnfoldLines: Boolean` | `Boolean` |
| `FoldLines: Boolean` | `Boolean` |
| `FoldLength: Integer` | `Integer` |

## Methods

```pascal
procedure AddStrings(Strings: TStrings);
procedure AddStdValues(ASrc: TStrings);
procedure AddValue(const AName, AValue: string);
procedure ConvertToStdValues(ADest: TStrings);
procedure Extract(const AName: string; ADest: TStrings);
function IndexOfName(const AName: string): Integer;
```

