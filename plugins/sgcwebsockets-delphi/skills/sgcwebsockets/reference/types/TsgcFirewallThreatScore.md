# TsgcFirewallThreatScore

kind: class
unit: sgcWebSocket_Server_Firewall

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `AutoBanThreshold: Integer` | `Integer` |
| `DecayPerHour: Integer` | `Integer` |
| `WeightSQLInjection: Integer` | `Integer` |
| `WeightXSS: Integer` | `Integer` |
| `WeightBruteForce: Integer` | `Integer` |
| `WeightFlood: Integer` | `Integer` |
| `WeightRateLimit: Integer` | `Integer` |
| `WeightPathTraversal: Integer` | `Integer` |
| `WeightCommandInjection: Integer` | `Integer` |
| `WeightGeoIP: Integer` | `Integer` |
| `WeightPayloadSize: Integer` | `Integer` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
```

