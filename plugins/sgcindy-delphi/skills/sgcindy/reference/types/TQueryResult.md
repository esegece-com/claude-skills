# TQueryResult

kind: class
unit: IdDNSResolver

## Properties

| Delphi | Type |
| --- | --- |
| `QueryClass: UInt16 (read-only)` | `UInt16` |
| `QueryType: UInt16 (read-only)` | `UInt16` |
| `DomainName: String (read-only)` | `String` |
| `Items[Index[Index: Integer]: TResultRecord` | [TResultRecord](./TResultRecord.md) |

## Methods

```pascal
procedure Assign(Source: TPersistent);
function Add(Answer: TIdBytes; var APos: Integer): TResultRecord;
procedure Clear;
procedure FilterBySection(const AKeep: TResultSections=[rsAnswer]);
procedure FilterByClass(const AKeep: TResultRecordClass);
```

