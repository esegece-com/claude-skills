# TIdDecoderUUE

unit: IdCoderUUE

Add `IdCoderUUE` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `FillChar: Char` | `Char` | `__property wchar_t FillChar;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Decode(ASrcStream: TStream; const ABytes: Integer = -1);
procedure DecodeBegin(ADestStream: TStream);
procedure DecodeEnd;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Decode(TStream * ASrcStream, const int ABytes = -1);
void __fastcall DecodeBegin(TStream * ADestStream);
void __fastcall DecodeEnd();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

