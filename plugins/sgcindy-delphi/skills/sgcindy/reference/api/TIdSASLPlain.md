# TIdSASLPlain

unit: IdSASLPlain

Add `IdSASLPlain` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `LoginAs: String` | `String` | `__property UnicodeString LoginAs;` |
| `UserPassProvider: TIdUserPassProvider` | [TIdUserPassProvider](../types/TIdUserPassProvider.md) | `__property TIdUserPassProvider * UserPassProvider;` |
| `SecurityLevel: UInt32 (read-only)` | `UInt32` | `__property UInt32 SecurityLevel /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function IsReadyToStart: Boolean;
function TryStartAuthenticate(const AHost, AProtocolName : string; var VInitialResponse: String): Boolean;
function StartAuthenticate(const AChallenge, AHost, AProtocolName : string) : String;
function ContinueAuthenticate(const ALastResponse, AHost, AProtocolName : string): string;
procedure FinishAuthenticate;
function IsAuthProtocolAvailable(AFeatStrings : TStrings) : Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
bool __fastcall IsReadyToStart();
bool __fastcall TryStartAuthenticate(const UnicodeString AHost, const UnicodeString AProtocolName, UnicodeString &VInitialResponse);
UnicodeString __fastcall StartAuthenticate(const UnicodeString AChallenge, const UnicodeString AHost, const UnicodeString AProtocolName);
UnicodeString __fastcall ContinueAuthenticate(const UnicodeString ALastResponse, const UnicodeString AHost, const UnicodeString AProtocolName);
void __fastcall FinishAuthenticate();
bool __fastcall IsAuthProtocolAvailable(TStrings * AFeatStrings);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

