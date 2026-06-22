# TIdServerBlockCipherIntercept

unit: IdBlockCipherIntercept

Add `IdBlockCipherIntercept` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `BlockSize: Integer` | `Integer` | `__property int BlockSize;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Init;
function Accept(AConnection: TComponent): TIdConnectionIntercept;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Init();
TIdConnectionIntercept * __fastcall Accept(TComponent * AConnection);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

