# TsgcWSAPIKeyManager

kind: class
unit: sgcWebSocket_Server_APIKeyManager

## Properties

| Delphi | Type |
| --- | --- |
| `Stats: TsgcAPIKeyStats (read-only)` | [TsgcAPIKeyStats](./TsgcAPIKeyStats.md) |
| `Enabled: Boolean` | `Boolean` |
| `Generation: TsgcAPIKeyGeneration` | [TsgcAPIKeyGeneration](./TsgcAPIKeyGeneration.md) |
| `Storage: TsgcAPIKeyStorage` | [TsgcAPIKeyStorage](./TsgcAPIKeyStorage.md) |
| `Hashing: TsgcAPIKeyHashing` | [TsgcAPIKeyHashing](./TsgcAPIKeyHashing.md) |
| `Scopes: TsgcAPIKeyScopeList` | [TsgcAPIKeyScopeList](./TsgcAPIKeyScopeList.md) |
| `Rotation: TsgcAPIKeyRotation` | [TsgcAPIKeyRotation](./TsgcAPIKeyRotation.md) |
| `Expiration: TsgcAPIKeyExpiration` | [TsgcAPIKeyExpiration](./TsgcAPIKeyExpiration.md) |
| `RateLimit: TsgcAPIKeyRateLimit` | [TsgcAPIKeyRateLimit](./TsgcAPIKeyRateLimit.md) |
| `Audit: TsgcAPIKeyAudit` | [TsgcAPIKeyAudit](./TsgcAPIKeyAudit.md) |
| `Validation: TsgcAPIKeyValidation` | [TsgcAPIKeyValidation](./TsgcAPIKeyValidation.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnKeyIssued: TsgcAPIKeyOnKeyIssued` | [TsgcAPIKeyOnKeyIssued](./TsgcAPIKeyOnKeyIssued.md) |
| `OnKeyValidated: TsgcAPIKeyOnKeyValidated` | [TsgcAPIKeyOnKeyValidated](./TsgcAPIKeyOnKeyValidated.md) |
| `OnKeyRevoked: TsgcAPIKeyOnKeyRevoked` | [TsgcAPIKeyOnKeyRevoked](./TsgcAPIKeyOnKeyRevoked.md) |
| `OnKeyRotated: TsgcAPIKeyOnKeyRotated` | [TsgcAPIKeyOnKeyRotated](./TsgcAPIKeyOnKeyRotated.md) |
| `OnKeyExpired: TsgcAPIKeyOnKeyExpired` | [TsgcAPIKeyOnKeyExpired](./TsgcAPIKeyOnKeyExpired.md) |
| `OnValidation: TsgcAPIKeyOnValidation` | [TsgcAPIKeyOnValidation](./TsgcAPIKeyOnValidation.md) |
| `OnAuditEvent: TsgcAPIKeyOnAuditEvent` | [TsgcAPIKeyOnAuditEvent](./TsgcAPIKeyOnAuditEvent.md) |

## Methods

```pascal
function IssueKey(const aOwner: string; const aScopes: TsgcAPIKeyScopes; aExpiresInSec: Integer = 0): string;
function ValidateKey(const aKey: string; const aRequiredScope: string = ''; const aIP: string = ''): Boolean;
function RevokeKey(const aKey: string; const aReason: string = ''): Boolean;
function RotateKey(const aOldKey: string; out aNewKey: string): Boolean;
function RenewKey(const aKey: string; aNewExpiresInSec: Integer): Boolean;
function GetKeyInfo(const aKey: string): TsgcAPIKeyInfo;
function GetKeysByOwner(const aOwner: string): TsgcAPIKeyArray;
function ListScopes(const aKey: string): TsgcAPIKeyScopes;
function IsExpired(const aKey: string): Boolean;
function IsRevoked(const aKey: string): Boolean;
function KeyExists(const aKey: string): Boolean;
procedure GrantScope(const aKey, aScope: string);
procedure RevokeScope(const aKey, aScope: string);
function HasScope(const aKey, aScope: string): Boolean;
function GetAuditLog(const aKey: string = ''; aMaxEntries: Integer = 100) : TsgcAPIKeyAuditEntries;
procedure ClearAuditLog(const aKey: string = '');
procedure SaveToFile(const aFileName: string = '');
procedure LoadFromFile(const aFileName: string = '');
procedure ExportKeys(aStream: TStream);
procedure ImportKeys(aStream: TStream);
procedure PurgeExpired;
function Count: Integer;
function IsConnectionAllowed(const aIP: string): Boolean;
function IsMessageAllowed(const aIP: string; const aMessage: string = ''): Boolean;
procedure RegisterConnection(const aIP: string);
procedure UnregisterConnection(const aIP: string);
function IsRequestAuthorized(const aHeaders: string; const aQueryString: string = ''; const aIP: string = ''; const aRequiredScope: string = ''): Boolean;
function ExtractKeyFromHeaders(const aHeaders: string): string;
function ExtractKeyFromQuery(const aQueryString: string): string;
```

