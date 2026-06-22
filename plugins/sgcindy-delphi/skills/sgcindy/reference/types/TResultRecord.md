# TResultRecord

kind: class
unit: IdDNSResolver

## Properties

| Delphi | Type |
| --- | --- |
| `RecType: TQueryRecordTypes (read-only)` | `TQueryRecordTypes` |
| `RecClass: UInt16 (read-only)` | `UInt16` |
| `Name: string (read-only)` | `string` |
| `TTL: UInt32 (read-only)` | `UInt32` |
| `RDataLength: Integer (read-only)` | `Integer` |
| `RData: TIdBytes (read-only)` | `TIdBytes` |
| `Section: TResultSection (read-only)` | `TResultSection` |
| `TypeCode: UInt16 (read-only)` | `UInt16` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
procedure Parse(CompleteMessage: TIdBytes; APos: Integer);
```

