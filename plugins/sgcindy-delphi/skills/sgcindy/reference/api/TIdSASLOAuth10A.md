# TIdSASLOAuth10A

unit: IdSASLOAuth

Add `IdSASLOAuth` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `UserPassProvider: TIdUserPassProvider` | [TIdUserPassProvider](../types/TIdUserPassProvider.md) | `__property TIdUserPassProvider * UserPassProvider;` |
| `SecurityLevel: UInt32 (read-only)` | `UInt32` | `__property UInt32 SecurityLevel /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnGetAccessToken: TIdSASLOAuth10ATokenEvent` | [TIdSASLOAuth10ATokenEvent](../types/TIdSASLOAuth10ATokenEvent.md) | `__property TIdSASLOAuth10ATokenEvent OnGetAccessToken;` |

## Methods

Delphi

```pascal
function TryStartAuthenticate(const AHost: string; const APort: TIdPort; const AProtocolName : string; var VInitialResponse: String): Boolean;
function StartAuthenticate(const AChallenge, AHost: string; const APort: TIdPort; const AProtocolName : string) : String;
function ContinueAuthenticate(const ALastResponse, AHost: string; const APort: TIdPort; const AProtocolName : String): String;
function IsReadyToStart: Boolean;
procedure FinishAuthenticate;
function IsAuthProtocolAvailable(AFeatStrings : TStrings) : Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
bool __fastcall TryStartAuthenticate(const UnicodeString AHost, const TIdPort * APort, const UnicodeString AProtocolName, UnicodeString &VInitialResponse);
UnicodeString __fastcall StartAuthenticate(const UnicodeString AChallenge, const UnicodeString AHost, const TIdPort * APort, const UnicodeString AProtocolName);
UnicodeString __fastcall ContinueAuthenticate(const UnicodeString ALastResponse, const UnicodeString AHost, const TIdPort * APort, const UnicodeString AProtocolName);
bool __fastcall IsReadyToStart();
void __fastcall FinishAuthenticate();
bool __fastcall IsAuthProtocolAvailable(TStrings * AFeatStrings);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

