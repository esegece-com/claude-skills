# TsgcWSConnectionServer

kind: class
unit: sgcWebSocket_Server

## Properties

| Delphi | Type |
| --- | --- |
| `ServerOriginsAllowed: String` | `String` |
| `ServerSSL: Boolean` | `Boolean` |
| `EnforceWebSocketVersion: Boolean` | `Boolean` |
| `ValidateWebSocketKey: Boolean` | `Boolean` |
| `HandShake: TsgcWSHandShakeServer (read-only)` | [TsgcWSHandShakeServer](./TsgcWSHandShakeServer.md) |
| `Authentication: TsgcWSConnectionAuthentication` | [TsgcWSConnectionAuthentication](./TsgcWSConnectionAuthentication.md) |
| `IOHandlerType: TwsIOHandler` | [TwsIOHandler](./TwsIOHandler.md) |
| `ReadTimeOut: Integer` | `Integer` |
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
procedure SendResponseHTTP(const aContent, aContentType: String);
procedure DisconnectPeer(aCallOnDisconnectIfClosed : Boolean = False);
procedure Disconnect;
procedure Close;
```

