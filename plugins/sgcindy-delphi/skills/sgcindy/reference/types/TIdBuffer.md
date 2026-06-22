# TIdBuffer

kind: class
unit: IdBuffer

## Properties

| Delphi | Type |
| --- | --- |
| `Capacity: Integer` | `Integer` |
| `Encoding: IIdTextEncoding` | [IIdTextEncoding](./IIdTextEncoding.md) |
| `AnsiEncoding: IIdTextEncoding` | [IIdTextEncoding](./IIdTextEncoding.md) |
| `GrowthFactor: Integer` | `Integer` |
| `Size: Integer (read-only)` | `Integer` |
| `AsString: string (read-only)` | `string` |

## Methods

```pascal
procedure Clear;
procedure CompactHead(ACanShrink: Boolean = True);
function Extract(AByteCount: Integer = -1; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ExtractToString(AByteCount: Integer = -1; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure ExtractToStream(const AStream: TStream; AByteCount: Integer = -1; const AIndex: Integer = -1);
procedure ExtractToIdBuffer(ABuffer: TIdBuffer; AByteCount: Integer = -1; const AIndex : Integer = -1);
procedure ExtractToBytes(var VBytes: TIdBytes; AByteCount: Integer = -1; AAppend: Boolean = True; AIndex : Integer = -1);
function ExtractToUInt8(const AIndex : Integer): UInt8;
function ExtractToByte(const AIndex : Integer): UInt8;
function ExtractToUInt16(const AIndex : Integer; AConvert: Boolean = True): UInt16;
function ExtractToWord(const AIndex : Integer): UInt16;
function ExtractToUInt32(const AIndex : Integer; AConvert: Boolean = True): UInt32;
function ExtractToLongWord(const AIndex : Integer): UInt32;
function ExtractToUInt64(const AIndex : Integer; AConvert: Boolean = True): TIdUInt64;
procedure ExtractToIPv6(const AIndex : Integer; var VAddress: TIdIPv6Address);
function IndexOf(const AByte: Byte; AStartPos: Integer = 0): Integer;
function PeekByte(AIndex: Integer): Byte;
procedure Remove(AByteCount: Integer);
procedure SaveToStream(const AStream: TStream);
procedure Write(const AString: string; AByteEncoding: IIdTextEncoding = nil; const ADestIndex: Integer = -1 ; ASrcEncoding: IIdTextEncoding = nil );
```

