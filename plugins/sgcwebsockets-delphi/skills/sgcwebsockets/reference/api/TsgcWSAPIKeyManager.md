# TsgcWSAPIKeyManager

unit: sgcWebSocket_Server_APIKeyManager
Edition: requires SGC_APIKEYMANAGER

Add `sgcWebSocket_Server_APIKeyManager` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Stats: TsgcAPIKeyStats (read-only)` | [TsgcAPIKeyStats](../types/TsgcAPIKeyStats.md) | `__property TsgcAPIKeyStats * Stats /* read-only */;` |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `Generation: TsgcAPIKeyGeneration` | [TsgcAPIKeyGeneration](../types/TsgcAPIKeyGeneration.md) | `__property TsgcAPIKeyGeneration * Generation;` |
| `Storage: TsgcAPIKeyStorage` | [TsgcAPIKeyStorage](../types/TsgcAPIKeyStorage.md) | `__property TsgcAPIKeyStorage * Storage;` |
| `Hashing: TsgcAPIKeyHashing` | [TsgcAPIKeyHashing](../types/TsgcAPIKeyHashing.md) | `__property TsgcAPIKeyHashing * Hashing;` |
| `Scopes: TsgcAPIKeyScopeList` | [TsgcAPIKeyScopeList](../types/TsgcAPIKeyScopeList.md) | `__property TsgcAPIKeyScopeList * Scopes;` |
| `Rotation: TsgcAPIKeyRotation` | [TsgcAPIKeyRotation](../types/TsgcAPIKeyRotation.md) | `__property TsgcAPIKeyRotation * Rotation;` |
| `Expiration: TsgcAPIKeyExpiration` | [TsgcAPIKeyExpiration](../types/TsgcAPIKeyExpiration.md) | `__property TsgcAPIKeyExpiration * Expiration;` |
| `RateLimit: TsgcAPIKeyRateLimit` | [TsgcAPIKeyRateLimit](../types/TsgcAPIKeyRateLimit.md) | `__property TsgcAPIKeyRateLimit * RateLimit;` |
| `Audit: TsgcAPIKeyAudit` | [TsgcAPIKeyAudit](../types/TsgcAPIKeyAudit.md) | `__property TsgcAPIKeyAudit * Audit;` |
| `Validation: TsgcAPIKeyValidation` | [TsgcAPIKeyValidation](../types/TsgcAPIKeyValidation.md) | `__property TsgcAPIKeyValidation * Validation;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnKeyIssued: TsgcAPIKeyOnKeyIssued` | [TsgcAPIKeyOnKeyIssued](../types/TsgcAPIKeyOnKeyIssued.md) | `__property TsgcAPIKeyOnKeyIssued * OnKeyIssued;` |
| `OnKeyValidated: TsgcAPIKeyOnKeyValidated` | [TsgcAPIKeyOnKeyValidated](../types/TsgcAPIKeyOnKeyValidated.md) | `__property TsgcAPIKeyOnKeyValidated * OnKeyValidated;` |
| `OnKeyRevoked: TsgcAPIKeyOnKeyRevoked` | [TsgcAPIKeyOnKeyRevoked](../types/TsgcAPIKeyOnKeyRevoked.md) | `__property TsgcAPIKeyOnKeyRevoked * OnKeyRevoked;` |
| `OnKeyRotated: TsgcAPIKeyOnKeyRotated` | [TsgcAPIKeyOnKeyRotated](../types/TsgcAPIKeyOnKeyRotated.md) | `__property TsgcAPIKeyOnKeyRotated * OnKeyRotated;` |
| `OnKeyExpired: TsgcAPIKeyOnKeyExpired` | [TsgcAPIKeyOnKeyExpired](../types/TsgcAPIKeyOnKeyExpired.md) | `__property TsgcAPIKeyOnKeyExpired * OnKeyExpired;` |
| `OnValidation: TsgcAPIKeyOnValidation` | [TsgcAPIKeyOnValidation](../types/TsgcAPIKeyOnValidation.md) | `__property TsgcAPIKeyOnValidation * OnValidation;` |
| `OnAuditEvent: TsgcAPIKeyOnAuditEvent` | [TsgcAPIKeyOnAuditEvent](../types/TsgcAPIKeyOnAuditEvent.md) | `__property TsgcAPIKeyOnAuditEvent OnAuditEvent;` |

## Methods

Delphi

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

C++Builder

```cpp
UnicodeString __fastcall IssueKey(const UnicodeString aOwner, const TsgcAPIKeyScopes * aScopes, int aExpiresInSec = 0);
bool __fastcall ValidateKey(const UnicodeString aKey, const UnicodeString aRequiredScope = '', const UnicodeString aIP = '');
bool __fastcall RevokeKey(const UnicodeString aKey, const UnicodeString aReason = '');
bool __fastcall RotateKey(const UnicodeString aOldKey, UnicodeString &aNewKey);
bool __fastcall RenewKey(const UnicodeString aKey, int aNewExpiresInSec);
TsgcAPIKeyInfo * __fastcall GetKeyInfo(const UnicodeString aKey);
TsgcAPIKeyArray * __fastcall GetKeysByOwner(const UnicodeString aOwner);
TsgcAPIKeyScopes * __fastcall ListScopes(const UnicodeString aKey);
bool __fastcall IsExpired(const UnicodeString aKey);
bool __fastcall IsRevoked(const UnicodeString aKey);
bool __fastcall KeyExists(const UnicodeString aKey);
void __fastcall GrantScope(const UnicodeString aKey, const UnicodeString aScope);
void __fastcall RevokeScope(const UnicodeString aKey, const UnicodeString aScope);
bool __fastcall HasScope(const UnicodeString aKey, const UnicodeString aScope);
TsgcAPIKeyAuditEntries * __fastcall GetAuditLog(const UnicodeString aKey = '', int aMaxEntries = 100);
void __fastcall ClearAuditLog(const UnicodeString aKey = '');
void __fastcall SaveToFile(const UnicodeString aFileName = '');
void __fastcall LoadFromFile(const UnicodeString aFileName = '');
void __fastcall ExportKeys(TStream * aStream);
void __fastcall ImportKeys(TStream * aStream);
void __fastcall PurgeExpired();
int __fastcall Count();
bool __fastcall IsConnectionAllowed(const UnicodeString aIP);
bool __fastcall IsMessageAllowed(const UnicodeString aIP, const UnicodeString aMessage = '');
void __fastcall RegisterConnection(const UnicodeString aIP);
void __fastcall UnregisterConnection(const UnicodeString aIP);
bool __fastcall IsRequestAuthorized(const UnicodeString aHeaders, const UnicodeString aQueryString = '', const UnicodeString aIP = '', const UnicodeString aRequiredScope = '');
UnicodeString __fastcall ExtractKeyFromHeaders(const UnicodeString aHeaders);
UnicodeString __fastcall ExtractKeyFromQuery(const UnicodeString aQueryString);
```

