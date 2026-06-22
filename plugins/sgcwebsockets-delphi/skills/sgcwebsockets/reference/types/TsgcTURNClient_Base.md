# TsgcTURNClient_Base

kind: class
unit: sgcP2P_TURN_Client

## Properties

| Delphi | Type |
| --- | --- |
| `TURNOptions: TsgcTURNClient_Options` | [TsgcTURNClient_Options](./TsgcTURNClient_Options.md) |
| `Allocation: TsgcTURNClient_Allocation` | [TsgcTURNClient_Allocation](./TsgcTURNClient_Allocation.md) |
| `RetransmissionOptions: TsgcSTUNPRetransmissionClient_Options` | [TsgcSTUNPRetransmissionClient_Options](./TsgcSTUNPRetransmissionClient_Options.md) |
| `Host: string` | `string` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` |
| `LogFile: TsgcSTUNLogFile` | [TsgcSTUNLogFile](./TsgcSTUNLogFile.md) |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](./TwsNotifyEvent.md) |
| `Port: Integer` | `Integer` |
| `STUNOptions: TsgcSTUNClient_Options` | [TsgcSTUNClient_Options](./TsgcSTUNClient_Options.md) |
| `Transport: TsgcStunTransport` | [TsgcStunTransport](./TsgcStunTransport.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnTURNAllocate: TsgcTURNAllocateEvent` | [TsgcTURNAllocateEvent](./TsgcTURNAllocateEvent.md) |
| `OnTURNChannelBind: TsgcTURNChannelBindEvent` | [TsgcTURNChannelBindEvent](./TsgcTURNChannelBindEvent.md) |
| `OnTURNChannelData: TsgcTURNDataChannelEvent` | [TsgcTURNDataChannelEvent](./TsgcTURNDataChannelEvent.md) |
| `OnTURNRefresh: TsgcTURNRefreshEvent` | [TsgcTURNRefreshEvent](./TsgcTURNRefreshEvent.md) |
| `OnTURNCreatePermission: TsgcTURNCreatePermissionEvent` | [TsgcTURNCreatePermissionEvent](./TsgcTURNCreatePermissionEvent.md) |
| `OnTURNDataIndication: TsgcTURNDataIndicationEvent` | [TsgcTURNDataIndicationEvent](./TsgcTURNDataIndicationEvent.md) |
| `OnTURNICMPIndication: TsgcTURNICMPIndicationEvent` | [TsgcTURNICMPIndicationEvent](./TsgcTURNICMPIndicationEvent.md) |
| `OnSTUNException: TsgcSTUNExceptionEvent` | [TsgcSTUNExceptionEvent](./TsgcSTUNExceptionEvent.md) |
| `OnSTUNResponseError: TsgcSTUNResponseErrorEvent` | [TsgcSTUNResponseErrorEvent](./TsgcSTUNResponseErrorEvent.md) |
| `OnSTUNResponseSuccess: TsgcSTUNResponseSuccessEvent` | [TsgcSTUNResponseSuccessEvent](./TsgcSTUNResponseSuccessEvent.md) |
| `OnSTUNBeforeSend: TsgcSTUNBeforeSendEvent` | [TsgcSTUNBeforeSendEvent](./TsgcSTUNBeforeSendEvent.md) |
| `OnSTUNUnknownMessage: TsgcSTUNUnknownMessageEvent` | [TsgcSTUNUnknownMessageEvent](./TsgcSTUNUnknownMessageEvent.md) |
| `OnDTLSRead: TsgcSTUNDTLSReadEvent` | [TsgcSTUNDTLSReadEvent](./TsgcSTUNDTLSReadEvent.md) |

## Methods

```pascal
procedure Allocate;
procedure Refresh(aLifetime: Cardinal);
procedure SendIndication(const aPeerIP: string; aPeerPort: Word; const aData: string);
procedure SendChannelData(const aChannelID: Word; const aData: string);
procedure ChannelBind(const aPeerIP: string; aPeerPort: Word);
procedure CreatePermission(const aPeerIP: string);
procedure Clear;
function SendRequest: Boolean;
procedure WriteData(const aBytes: TBytes);
```

