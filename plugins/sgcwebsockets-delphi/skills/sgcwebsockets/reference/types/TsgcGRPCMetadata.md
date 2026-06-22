# TsgcGRPCMetadata

kind: class
unit: sgcGRPC_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Items: TStringList (read-only)` | `TStringList` |

## Methods

```pascal
procedure Add(const aKey, aValue: string);
procedure AddBinary(const aKey: string; const aValue: TBytes);
function GetValue(const aKey: string): string;
function GetBinaryValue(const aKey: string): TBytes;
function ContainsKey(const aKey: string): Boolean;
procedure Remove(const aKey: string);
procedure Clear;
function Count: Integer;
function GetKey(aIndex: Integer): string;
function GetValueByIndex(aIndex: Integer): string;
procedure Assign(aSource: TsgcGRPCMetadata);
```

