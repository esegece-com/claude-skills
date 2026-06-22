# TsgcWSRateLimiter

kind: class
unit: sgcWebSocket_Server_RateLimiter

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `StorageFile: string` | `string` |
| `TokenBucket: TsgcRateLimitTokenBucket` | [TsgcRateLimitTokenBucket](./TsgcRateLimitTokenBucket.md) |
| `SlidingWindow: TsgcRateLimitSlidingWindow` | [TsgcRateLimitSlidingWindow](./TsgcRateLimitSlidingWindow.md) |
| `FixedWindow: TsgcRateLimitFixedWindow` | [TsgcRateLimitFixedWindow](./TsgcRateLimitFixedWindow.md) |
| `PerIP: TsgcRateLimitRule` | [TsgcRateLimitRule](./TsgcRateLimitRule.md) |
| `PerAPIKey: TsgcRateLimitRule` | [TsgcRateLimitRule](./TsgcRateLimitRule.md) |
| `PerUser: TsgcRateLimitRule` | [TsgcRateLimitRule](./TsgcRateLimitRule.md) |
| `PerEndpoint: TsgcRateLimitRuleList` | [TsgcRateLimitRuleList](./TsgcRateLimitRuleList.md) |
| `Quotas: TsgcRateLimitQuotaList` | [TsgcRateLimitQuotaList](./TsgcRateLimitQuotaList.md) |
| `BurstProtection: TsgcRateLimitBurst` | [TsgcRateLimitBurst](./TsgcRateLimitBurst.md) |
| `Response: TsgcRateLimitResponse` | [TsgcRateLimitResponse](./TsgcRateLimitResponse.md) |
| `Stats: TsgcRateLimitStats (read-only)` | [TsgcRateLimitStats](./TsgcRateLimitStats.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnThrottled: TsgcRateLimitOnThrottled` | [TsgcRateLimitOnThrottled](./TsgcRateLimitOnThrottled.md) |
| `OnQuotaExceeded: TsgcRateLimitOnQuotaExceeded` | [TsgcRateLimitOnQuotaExceeded](./TsgcRateLimitOnQuotaExceeded.md) |
| `OnStateChange: TsgcRateLimitOnStateChange` | [TsgcRateLimitOnStateChange](./TsgcRateLimitOnStateChange.md) |

## Methods

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

