# TsgcWSFirewall

kind: class
unit: sgcWebSocket_Server_Firewall

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `Blacklist: TsgcFirewallIPList` | [TsgcFirewallIPList](./TsgcFirewallIPList.md) |
| `Whitelist: TsgcFirewallIPList` | [TsgcFirewallIPList](./TsgcFirewallIPList.md) |
| `BruteForce: TsgcFirewallBruteForce` | [TsgcFirewallBruteForce](./TsgcFirewallBruteForce.md) |
| `SQLInjection: TsgcFirewallSQLInjection` | [TsgcFirewallSQLInjection](./TsgcFirewallSQLInjection.md) |
| `XSS: TsgcFirewallXSS` | [TsgcFirewallXSS](./TsgcFirewallXSS.md) |
| `RateLimit: TsgcFirewallRateLimit` | [TsgcFirewallRateLimit](./TsgcFirewallRateLimit.md) |
| `FloodProtection: TsgcFirewallFloodProtection` | [TsgcFirewallFloodProtection](./TsgcFirewallFloodProtection.md) |
| `PayloadLimit: TsgcFirewallPayloadLimit` | [TsgcFirewallPayloadLimit](./TsgcFirewallPayloadLimit.md) |
| `PathTraversal: TsgcFirewallPathTraversal` | [TsgcFirewallPathTraversal](./TsgcFirewallPathTraversal.md) |
| `CommandInjection: TsgcFirewallCommandInjection` | [TsgcFirewallCommandInjection](./TsgcFirewallCommandInjection.md) |
| `ThreatScore: TsgcFirewallThreatScore` | [TsgcFirewallThreatScore](./TsgcFirewallThreatScore.md) |
| `BanEscalation: TsgcFirewallBanEscalation` | [TsgcFirewallBanEscalation](./TsgcFirewallBanEscalation.md) |
| `GeoIP: TsgcFirewallGeoIP` | [TsgcFirewallGeoIP](./TsgcFirewallGeoIP.md) |
| `WebSocketProtection: TsgcFirewallWebSocketProtection` | [TsgcFirewallWebSocketProtection](./TsgcFirewallWebSocketProtection.md) |
| `CustomRules: TsgcFirewallRules` | [TsgcFirewallRules](./TsgcFirewallRules.md) |
| `BotDetection: TsgcFirewallBotDetection` | [TsgcFirewallBotDetection](./TsgcFirewallBotDetection.md) |
| `Stats: TsgcFirewallStats (read-only)` | [TsgcFirewallStats](./TsgcFirewallStats.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnFiltered: TsgcFirewallOnFiltered` | [TsgcFirewallOnFiltered](./TsgcFirewallOnFiltered.md) |
| `OnViolation: TsgcFirewallOnViolation` | [TsgcFirewallOnViolation](./TsgcFirewallOnViolation.md) |
| `OnResolveCountry: TsgcFirewallOnResolveCountry` | [TsgcFirewallOnResolveCountry](./TsgcFirewallOnResolveCountry.md) |
| `OnThreatScoreChanged: TsgcFirewallOnThreatScoreChanged` | [TsgcFirewallOnThreatScoreChanged](./TsgcFirewallOnThreatScoreChanged.md) |
| `OnBotDetected: TsgcFirewallOnBotDetected` | [TsgcFirewallOnBotDetected](./TsgcFirewallOnBotDetected.md) |
| `OnResolveBot: TsgcFirewallOnResolveBot` | [TsgcFirewallOnResolveBot](./TsgcFirewallOnResolveBot.md) |

## Methods

```pascal
function IsConnectionAllowed(const aIP: string): Boolean;
function IsMessageAllowed(const aIP: string; const aMessage: string): Boolean;
procedure RegisterConnection(const aIP: string);
procedure UnregisterConnection(const aIP: string);
procedure RegisterFailedAttempt(const aIP: string);
procedure BanIP(const aIP: string; aDurationSec: Integer = 0);
procedure UnbanIP(const aIP: string);
function IsBanned(const aIP: string): Boolean;
procedure ClearBans;
procedure ClearTracking;
procedure SaveBansToFile(const aFileName: string);
procedure LoadBansFromFile(const aFileName: string);
procedure SaveBansToStream(aStream: TStream);
procedure LoadBansFromStream(aStream: TStream);
procedure LoadGeoIPDatabase(const aFileName: string);
function LookupCountry(const aIP: string): string;
function IsOriginAllowed(const aOrigin: string): Boolean;
function IsFrameSizeAllowed(aSize: Integer): Boolean;
function IsSubprotocolAllowed(const aSubprotocol: string): Boolean;
function GetThreatScore(const aIP: string): Integer;
procedure ResetThreatScore(const aIP: string);
function GetTopThreats(aCount: Integer): TStringList;
function GetBotClassification(const aIP: string): TsgcBotClassification;
```

