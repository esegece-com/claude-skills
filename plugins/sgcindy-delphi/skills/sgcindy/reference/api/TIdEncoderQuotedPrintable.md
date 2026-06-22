# TIdEncoderQuotedPrintable

unit: IdCoderQuotedPrintable

Add `IdCoderQuotedPrintable` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
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

