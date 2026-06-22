# TDNSHeader

kind: class
unit: IdDNSCommon

## Properties

| Delphi | Type |
| --- | --- |
| `ID: UInt16` | `UInt16` |
| `Qr: UInt16` | `UInt16` |
| `OpCode: UInt16` | `UInt16` |
| `AA: UInt16` | `UInt16` |
| `TC: UInt16` | `UInt16` |
| `RD: UInt16` | `UInt16` |
| `RA: UInt16` | `UInt16` |
| `RCode: UInt16` | `UInt16` |
| `BitCode: UInt16` | `UInt16` |
| `QDCount: UInt16` | `UInt16` |
| `ANCount: UInt16` | `UInt16` |
| `NSCount: UInt16` | `UInt16` |
| `ARCount: UInt16` | `UInt16` |

## Methods

```pascal
procedure ClearByteCode;
function ParseQuery(Data : TIdBytes) : integer;
function GenerateBinaryHeader : TIdBytes;
```

