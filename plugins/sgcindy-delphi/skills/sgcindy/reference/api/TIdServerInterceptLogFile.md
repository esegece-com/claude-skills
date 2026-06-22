# TIdServerInterceptLogFile

unit: IdServerInterceptLogFile

Add `IdServerInterceptLogFile` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Filename: string` | `string` | `__property UnicodeString Filename;` |
| `LogTime: Boolean` | `Boolean` | `__property bool LogTime;` |
| `ReplaceCRLF: Boolean` | `Boolean` | `__property bool ReplaceCRLF;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Init;
procedure DoLogWriteString(const AText: string);
function Accept(AConnection: TComponent): TIdConnectionIntercept;
procedure LogWriteString(const AText: string);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Init();
void __fastcall DoLogWriteString(const UnicodeString AText);
TIdConnectionIntercept * __fastcall Accept(TComponent * AConnection);
void __fastcall LogWriteString(const UnicodeString AText);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

