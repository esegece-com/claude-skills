# TsgcFirewallBotDetection

kind: class
unit: sgcWebSocket_Server_Firewall

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `KnownBotsFile: string` | `string` |
| `Datacenter: TsgcFirewallBotDatacenter` | [TsgcFirewallBotDatacenter](./TsgcFirewallBotDatacenter.md) |
| `ReverseDNS: TsgcFirewallBotReverseDNS` | [TsgcFirewallBotReverseDNS](./TsgcFirewallBotReverseDNS.md) |
| `DNSBL: TsgcFirewallBotDNSBL` | [TsgcFirewallBotDNSBL](./TsgcFirewallBotDNSBL.md) |
| `CacheDurationSec: Integer` | `Integer` |
| `DNSTimeoutMS: Integer` | `Integer` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
```

