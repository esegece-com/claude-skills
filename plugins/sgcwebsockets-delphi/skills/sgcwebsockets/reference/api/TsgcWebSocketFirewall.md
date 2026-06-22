# TsgcWebSocketFirewall

unit: sgcWebSocket
Edition: requires SGC_FIREWALL

Add `sgcWebSocket` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `Blacklist: TsgcFirewallIPList` | [TsgcFirewallIPList](../types/TsgcFirewallIPList.md) | `__property TsgcFirewallIPList * Blacklist;` |
| `Whitelist: TsgcFirewallIPList` | [TsgcFirewallIPList](../types/TsgcFirewallIPList.md) | `__property TsgcFirewallIPList * Whitelist;` |
| `BruteForce: TsgcFirewallBruteForce` | [TsgcFirewallBruteForce](../types/TsgcFirewallBruteForce.md) | `__property TsgcFirewallBruteForce * BruteForce;` |
| `SQLInjection: TsgcFirewallSQLInjection` | [TsgcFirewallSQLInjection](../types/TsgcFirewallSQLInjection.md) | `__property TsgcFirewallSQLInjection * SQLInjection;` |
| `XSS: TsgcFirewallXSS` | [TsgcFirewallXSS](../types/TsgcFirewallXSS.md) | `__property TsgcFirewallXSS * XSS;` |
| `RateLimit: TsgcFirewallRateLimit` | [TsgcFirewallRateLimit](../types/TsgcFirewallRateLimit.md) | `__property TsgcFirewallRateLimit * RateLimit;` |
| `FloodProtection: TsgcFirewallFloodProtection` | [TsgcFirewallFloodProtection](../types/TsgcFirewallFloodProtection.md) | `__property TsgcFirewallFloodProtection * FloodProtection;` |
| `PayloadLimit: TsgcFirewallPayloadLimit` | [TsgcFirewallPayloadLimit](../types/TsgcFirewallPayloadLimit.md) | `__property TsgcFirewallPayloadLimit * PayloadLimit;` |
| `PathTraversal: TsgcFirewallPathTraversal` | [TsgcFirewallPathTraversal](../types/TsgcFirewallPathTraversal.md) | `__property TsgcFirewallPathTraversal * PathTraversal;` |
| `CommandInjection: TsgcFirewallCommandInjection` | [TsgcFirewallCommandInjection](../types/TsgcFirewallCommandInjection.md) | `__property TsgcFirewallCommandInjection * CommandInjection;` |
| `ThreatScore: TsgcFirewallThreatScore` | [TsgcFirewallThreatScore](../types/TsgcFirewallThreatScore.md) | `__property TsgcFirewallThreatScore * ThreatScore;` |
| `BanEscalation: TsgcFirewallBanEscalation` | [TsgcFirewallBanEscalation](../types/TsgcFirewallBanEscalation.md) | `__property TsgcFirewallBanEscalation * BanEscalation;` |
| `GeoIP: TsgcFirewallGeoIP` | [TsgcFirewallGeoIP](../types/TsgcFirewallGeoIP.md) | `__property TsgcFirewallGeoIP * GeoIP;` |
| `WebSocketProtection: TsgcFirewallWebSocketProtection` | [TsgcFirewallWebSocketProtection](../types/TsgcFirewallWebSocketProtection.md) | `__property TsgcFirewallWebSocketProtection * WebSocketProtection;` |
| `CustomRules: TsgcFirewallRules` | [TsgcFirewallRules](../types/TsgcFirewallRules.md) | `__property TsgcFirewallRules * CustomRules;` |
| `BotDetection: TsgcFirewallBotDetection` | [TsgcFirewallBotDetection](../types/TsgcFirewallBotDetection.md) | `__property TsgcFirewallBotDetection * BotDetection;` |
| `Stats: TsgcFirewallStats (read-only)` | [TsgcFirewallStats](../types/TsgcFirewallStats.md) | `__property TsgcFirewallStats * Stats /* read-only */;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnFiltered: TsgcFirewallOnFiltered` | [TsgcFirewallOnFiltered](../types/TsgcFirewallOnFiltered.md) | `__property TsgcFirewallOnFiltered * OnFiltered;` |
| `OnViolation: TsgcFirewallOnViolation` | [TsgcFirewallOnViolation](../types/TsgcFirewallOnViolation.md) | `__property TsgcFirewallOnViolation * OnViolation;` |
| `OnResolveCountry: TsgcFirewallOnResolveCountry` | [TsgcFirewallOnResolveCountry](../types/TsgcFirewallOnResolveCountry.md) | `__property TsgcFirewallOnResolveCountry * OnResolveCountry;` |
| `OnThreatScoreChanged: TsgcFirewallOnThreatScoreChanged` | [TsgcFirewallOnThreatScoreChanged](../types/TsgcFirewallOnThreatScoreChanged.md) | `__property TsgcFirewallOnThreatScoreChanged * OnThreatScoreChanged;` |
| `OnBotDetected: TsgcFirewallOnBotDetected` | [TsgcFirewallOnBotDetected](../types/TsgcFirewallOnBotDetected.md) | `__property TsgcFirewallOnBotDetected * OnBotDetected;` |
| `OnResolveBot: TsgcFirewallOnResolveBot` | [TsgcFirewallOnResolveBot](../types/TsgcFirewallOnResolveBot.md) | `__property TsgcFirewallOnResolveBot * OnResolveBot;` |

## Methods

Delphi

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

C++Builder

```cpp
bool __fastcall IsConnectionAllowed(const UnicodeString aIP);
bool __fastcall IsMessageAllowed(const UnicodeString aIP, const UnicodeString aMessage);
void __fastcall RegisterConnection(const UnicodeString aIP);
void __fastcall UnregisterConnection(const UnicodeString aIP);
void __fastcall RegisterFailedAttempt(const UnicodeString aIP);
void __fastcall BanIP(const UnicodeString aIP, int aDurationSec = 0);
void __fastcall UnbanIP(const UnicodeString aIP);
bool __fastcall IsBanned(const UnicodeString aIP);
void __fastcall ClearBans();
void __fastcall ClearTracking();
void __fastcall SaveBansToFile(const UnicodeString aFileName);
void __fastcall LoadBansFromFile(const UnicodeString aFileName);
void __fastcall SaveBansToStream(TStream * aStream);
void __fastcall LoadBansFromStream(TStream * aStream);
void __fastcall LoadGeoIPDatabase(const UnicodeString aFileName);
UnicodeString __fastcall LookupCountry(const UnicodeString aIP);
bool __fastcall IsOriginAllowed(const UnicodeString aOrigin);
bool __fastcall IsFrameSizeAllowed(int aSize);
bool __fastcall IsSubprotocolAllowed(const UnicodeString aSubprotocol);
int __fastcall GetThreatScore(const UnicodeString aIP);
void __fastcall ResetThreatScore(const UnicodeString aIP);
TStringList * __fastcall GetTopThreats(int aCount);
TsgcBotClassification * __fastcall GetBotClassification(const UnicodeString aIP);
```

