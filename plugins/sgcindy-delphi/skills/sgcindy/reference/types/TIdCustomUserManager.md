# TIdCustomUserManager

kind: class
unit: IdUserAccounts

## Properties

| Delphi | Type |
| --- | --- |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
function ChallengeUser(var VIsSafe : Boolean; const AUserName : String) : String;
function AuthenticateUser(const AUsername, APassword: String): Boolean;
procedure LogoffUser(AUserHandle: TIdUserHandle);
procedure UserDisconnected(const AUser : String);
function SendsChallange : Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

