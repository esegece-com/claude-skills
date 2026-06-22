# TIdSASLAnonymous

unit: IdSASLAnonymous

Add `IdSASLAnonymous` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TraceInfo: String` | `String` | `__property UnicodeString TraceInfo;` |
| `SecurityLevel: UInt32 (read-only)` | `UInt32` | `__property UInt32 SecurityLevel /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function IsReadyToStart: Boolean;
function TryStartAuthenticate(const AHost, AProtocolName : String; var VInitialResponse: String): Boolean;
function StartAuthenticate(const AChallenge, AHost, AProtocolName : String): String;
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

