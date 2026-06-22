# TsgcWSConnectionServer_Base

kind: class
unit: sgcWebSocket_Server_Base

## Properties

| Delphi | Type |
| --- | --- |
| `HandShake: TsgcWSHandShakeServer_Base (read-only)` | [TsgcWSHandShakeServer_Base](./TsgcWSHandShakeServer_Base.md) |
| `Authentication: TsgcWSConnectionAuthentication` | [TsgcWSConnectionAuthentication](./TsgcWSConnectionAuthentication.md) |
| `ServerOriginsAllowed: String` | `String` |
| `EnforceWebSocketVersion: Boolean` | `Boolean` |
| `ValidateWebSocketKey: Boolean` | `Boolean` |
| `MaxMessageSize: Int64` | `Int64` |
| `HeadersRequest: TIdHeaderList (read-only)` | [TIdHeaderList](./TIdHeaderList.md) |
| `Forward_HTTP: TsgcWSServerForwardHTTP (read-only)` | [TsgcWSServerForwardHTTP](./TsgcWSServerForwardHTTP.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnAuthentication: TsgcWSAuthenticationEvent` | [TsgcWSAuthenticationEvent](./TsgcWSAuthenticationEvent.md) |
| `OnSSECustomizeHeaders: TsgcWSSSECustomizeHeadersEvent` | `TsgcWSSSECustomizeHeadersEvent` |

## Methods

```pascal
procedure SetAuthenticationCloseCode(const aCloseCode: Integer);
procedure DisconnectPeer(aCallOnDisconnectIfClosed: Boolean = False);
procedure Disconnect;
procedure Close;
```

