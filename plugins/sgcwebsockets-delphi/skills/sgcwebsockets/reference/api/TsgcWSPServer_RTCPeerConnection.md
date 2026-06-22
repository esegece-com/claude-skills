# TsgcWSPServer_RTCPeerConnection

unit: sgcWebSocket_Protocols
Edition: Enterprise

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Server: TsgcWSHTTPServer` | [TsgcWSHTTPServer](../types/TsgcWSHTTPServer.md) | `__property TsgcWSHTTPServer * Server;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](../types/TsgcHTTP2ClientConnectEvent.md) | `__property TsgcHTTP2ClientConnectEvent OnConnect;` |
| `OnDisconnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnect;` |
| `OnError: TsgcHTTP3ErrorEvent` | `TsgcHTTP3ErrorEvent` | `__property TsgcHTTP3ErrorEvent OnError;` |
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnException: TsgcAMQP1OnExceptionEvent` | [TsgcAMQP1OnExceptionEvent](../types/TsgcAMQP1OnExceptionEvent.md) | `__property TsgcAMQP1OnExceptionEvent OnException;` |

