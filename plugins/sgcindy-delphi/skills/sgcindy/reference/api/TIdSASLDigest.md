# TIdSASLDigest

unit: IdSASLDigest

Add `IdSASLDigest` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `authzid: String` | `String` | `__property UnicodeString authzid;` |
| `UserPassProvider: TIdUserPassProvider` | [TIdUserPassProvider](../types/TIdUserPassProvider.md) | `__property TIdUserPassProvider * UserPassProvider;` |
| `SecurityLevel: UInt32 (read-only)` | `UInt32` | `__property UInt32 SecurityLevel /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function StartAuthenticate(const AChallenge, AHost, AProtocolName:string) : String;
function ContinueAuthenticate(const ALastResponse, AHost, AProtocolName : string): string;
function IsReadyToStart: Boolean;
function TryStartAuthenticate(const AHost, AProtocolName : string; var VInitialResponse: string): Boolean;
procedure FinishAuthenticate;
function IsAuthProtocolAvailable(AFeatStrings : TStrings) : Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
UnicodeString __fastcall StartAuthenticate(const UnicodeString AChallenge, const UnicodeString AHost, const UnicodeString AProtocolName);
UnicodeString __fastcall ContinueAuthenticate(const UnicodeString ALastResponse, const UnicodeString AHost, const UnicodeString AProtocolName);
bool __fastcall IsReadyToStart();
bool __fastcall TryStartAuthenticate(const UnicodeString AHost, const UnicodeString AProtocolName, UnicodeString &VInitialResponse);
void __fastcall FinishAuthenticate();
bool __fastcall IsAuthProtocolAvailable(TStrings * AFeatStrings);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

