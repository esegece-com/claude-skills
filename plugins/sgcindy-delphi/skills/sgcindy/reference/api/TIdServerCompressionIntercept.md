# TIdServerCompressionIntercept

unit: IdCompressionIntercept

Add `IdCompressionIntercept` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CompressionLevel: TIdCompressionLevel` | `TIdCompressionLevel` | `__property TIdCompressionLevel * CompressionLevel;` |
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

