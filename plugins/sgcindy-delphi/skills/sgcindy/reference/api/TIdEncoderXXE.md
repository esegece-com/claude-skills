# TIdEncoderXXE

unit: IdCoderXXE

Add `IdCoderXXE` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CodingTable: TIdBytes (read-only)` | `TIdBytes` | `__property TIdBytes * CodingTable /* read-only */;` |
| `FillChar: Char` | `Char` | `__property wchar_t FillChar;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Encode(ASrcStream, ADestStream: TStream; const ABytes: Integer = -1);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Encode(TStream * ASrcStream, TStream * ADestStream, const int ABytes = -1);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

