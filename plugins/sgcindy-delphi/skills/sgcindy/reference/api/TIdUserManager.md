# TIdUserManager

unit: IdUserAccounts

Add `IdUserAccounts` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Accounts: TIdUserAccounts` | [TIdUserAccounts](../types/TIdUserAccounts.md) | `__property TIdUserAccounts * Accounts;` |
| `Options: TIdCustomUserManagerOptions` | `TIdCustomUserManagerOptions` | `__property TIdCustomUserManagerOptions * Options;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeAuthentication: TIdUserManagerAuthenticationEvent` | [TIdUserManagerAuthenticationEvent](../types/TIdUserManagerAuthenticationEvent.md) | `__property TIdUserManagerAuthenticationEvent OnBeforeAuthentication;` |
| `OnAfterAuthentication: TIdUserManagerAuthenticationEvent` | [TIdUserManagerAuthenticationEvent](../types/TIdUserManagerAuthenticationEvent.md) | `__property TIdUserManagerAuthenticationEvent OnAfterAuthentication;` |

## Methods

Delphi

```pascal
function ChallengeUser(var VIsSafe : Boolean; const AUserName : String) : String;
function AuthenticateUser(const AUsername, APassword: String): Boolean;
procedure LogoffUser(AUserHandle: TIdUserHandle);
procedure UserDisconnected(const AUser : String);
function SendsChallange : Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
UnicodeString __fastcall ChallengeUser(bool &VIsSafe, const UnicodeString AUserName);
bool __fastcall AuthenticateUser(const UnicodeString AUsername, const UnicodeString APassword);
void __fastcall LogoffUser(TIdUserHandle * AUserHandle);
void __fastcall UserDisconnected(const UnicodeString AUser);
bool __fastcall SendsChallange();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

