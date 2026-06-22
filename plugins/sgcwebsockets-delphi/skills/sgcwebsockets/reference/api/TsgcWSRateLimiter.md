# TsgcWSRateLimiter

unit: sgcWebSocket_Server_RateLimiter
Edition: Professional

Add `sgcWebSocket_Server_RateLimiter` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `StorageFile: string` | `string` | `__property UnicodeString StorageFile;` |
| `TokenBucket: TsgcRateLimitTokenBucket` | [TsgcRateLimitTokenBucket](../types/TsgcRateLimitTokenBucket.md) | `__property TsgcRateLimitTokenBucket * TokenBucket;` |
| `SlidingWindow: TsgcRateLimitSlidingWindow` | [TsgcRateLimitSlidingWindow](../types/TsgcRateLimitSlidingWindow.md) | `__property TsgcRateLimitSlidingWindow * SlidingWindow;` |
| `FixedWindow: TsgcRateLimitFixedWindow` | [TsgcRateLimitFixedWindow](../types/TsgcRateLimitFixedWindow.md) | `__property TsgcRateLimitFixedWindow * FixedWindow;` |
| `PerIP: TsgcRateLimitRule` | [TsgcRateLimitRule](../types/TsgcRateLimitRule.md) | `__property TsgcRateLimitRule * PerIP;` |
| `PerAPIKey: TsgcRateLimitRule` | [TsgcRateLimitRule](../types/TsgcRateLimitRule.md) | `__property TsgcRateLimitRule * PerAPIKey;` |
| `PerUser: TsgcRateLimitRule` | [TsgcRateLimitRule](../types/TsgcRateLimitRule.md) | `__property TsgcRateLimitRule * PerUser;` |
| `PerEndpoint: TsgcRateLimitRuleList` | [TsgcRateLimitRuleList](../types/TsgcRateLimitRuleList.md) | `__property TsgcRateLimitRuleList * PerEndpoint;` |
| `Quotas: TsgcRateLimitQuotaList` | [TsgcRateLimitQuotaList](../types/TsgcRateLimitQuotaList.md) | `__property TsgcRateLimitQuotaList * Quotas;` |
| `BurstProtection: TsgcRateLimitBurst` | [TsgcRateLimitBurst](../types/TsgcRateLimitBurst.md) | `__property TsgcRateLimitBurst * BurstProtection;` |
| `Response: TsgcRateLimitResponse` | [TsgcRateLimitResponse](../types/TsgcRateLimitResponse.md) | `__property TsgcRateLimitResponse * Response;` |
| `Stats: TsgcRateLimitStats (read-only)` | [TsgcRateLimitStats](../types/TsgcRateLimitStats.md) | `__property TsgcRateLimitStats * Stats /* read-only */;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnThrottled: TsgcRateLimitOnThrottled` | [TsgcRateLimitOnThrottled](../types/TsgcRateLimitOnThrottled.md) | `__property TsgcRateLimitOnThrottled * OnThrottled;` |
| `OnQuotaExceeded: TsgcRateLimitOnQuotaExceeded` | [TsgcRateLimitOnQuotaExceeded](../types/TsgcRateLimitOnQuotaExceeded.md) | `__property TsgcRateLimitOnQuotaExceeded * OnQuotaExceeded;` |
| `OnStateChange: TsgcRateLimitOnStateChange` | [TsgcRateLimitOnStateChange](../types/TsgcRateLimitOnStateChange.md) | `__property TsgcRateLimitOnStateChange * OnStateChange;` |

## Methods

Delphi

```pascal
function IsAllowed(const aKey: string; aCost: Integer = 1): Boolean;
function Consume(const aKey: string; aCost: Integer = 1) : TsgcRateLimitResult;
procedure Reset(const aKey: string);
procedure ResetAll;
function GetRemaining(const aKey: string): Integer;
function GetRetryAfter(const aKey: string): Integer;
procedure SaveStateToFile(const aFileName: string);
procedure LoadStateFromFile(const aFileName: string);
procedure SaveStateToStream(aStream: TStream);
procedure LoadStateFromStream(aStream: TStream);
function IsConnectionAllowed(const aIP: string): Boolean;
function IsMessageAllowed(const aIP: string; const aMessage: string = ''): Boolean;
procedure RegisterConnection(const aIP: string);
procedure UnregisterConnection(const aIP: string);
```

C++Builder

```cpp
bool __fastcall IsAllowed(const UnicodeString aKey, int aCost = 1);
TsgcRateLimitResult * __fastcall Consume(const UnicodeString aKey, int aCost = 1);
void __fastcall Reset(const UnicodeString aKey);
void __fastcall ResetAll();
int __fastcall GetRemaining(const UnicodeString aKey);
int __fastcall GetRetryAfter(const UnicodeString aKey);
void __fastcall SaveStateToFile(const UnicodeString aFileName);
void __fastcall LoadStateFromFile(const UnicodeString aFileName);
void __fastcall SaveStateToStream(TStream * aStream);
void __fastcall LoadStateFromStream(TStream * aStream);
bool __fastcall IsConnectionAllowed(const UnicodeString aIP);
bool __fastcall IsMessageAllowed(const UnicodeString aIP, const UnicodeString aMessage = '');
void __fastcall RegisterConnection(const UnicodeString aIP);
void __fastcall UnregisterConnection(const UnicodeString aIP);
```

