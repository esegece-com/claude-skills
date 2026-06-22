# TsgcAI_Database_Vector

kind: class
unit: sgcAI_DB_Vector

## Properties

| Delphi | Type |
| --- | --- |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnBeginAddData: TsgcAIOnBeginAddData` | [TsgcAIOnBeginAddData](./TsgcAIOnBeginAddData.md) |

## Methods

```pascal
procedure BeginAddData;
procedure EndAddData;
procedure AddData(const aInput, aVector: string);
function QueryData(const aVector: string): string;
```

