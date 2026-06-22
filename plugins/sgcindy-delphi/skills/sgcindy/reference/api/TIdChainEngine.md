# TIdChainEngine

unit: IdIOHandlerChain

Add `IdIOHandlerChain` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure AddWork(AWorkOpUnit: TIdWorkOpUnit);
procedure BeforeDestruction;
procedure RemoveSocket(AIOHandler: TIdIOHandlerChain);
procedure SocketAccepted(AIOHandler: TIdIOHandlerChain);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall AddWork(TIdWorkOpUnit * AWorkOpUnit);
void __fastcall BeforeDestruction();
void __fastcall RemoveSocket(TIdIOHandlerChain * AIOHandler);
void __fastcall SocketAccepted(TIdIOHandlerChain * AIOHandler);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

