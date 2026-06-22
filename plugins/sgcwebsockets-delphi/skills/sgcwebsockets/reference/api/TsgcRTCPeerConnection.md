# TsgcRTCPeerConnection

unit: sgcP2P
Edition: Enterprise

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `RTCOptions: TsgcRTCPeerConnection_Options` | [TsgcRTCPeerConnection_Options](../types/TsgcRTCPeerConnection_Options.md) | `__property TsgcRTCPeerConnection_Options * RTCOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnRTCWebSocketBeforeConnect: TsgcRTCWebSocketBeforeConnectEvent` | [TsgcRTCWebSocketBeforeConnectEvent](../types/TsgcRTCWebSocketBeforeConnectEvent.md) | `__property TsgcRTCWebSocketBeforeConnectEvent OnRTCWebSocketBeforeConnect;` |
| `OnRTCWebSocketConnect: TsgcRTCWebSocketConnectEvent` | [TsgcRTCWebSocketConnectEvent](../types/TsgcRTCWebSocketConnectEvent.md) | `__property TsgcRTCWebSocketConnectEvent OnRTCWebSocketConnect;` |
| `OnRTCWebSocketDisconnect: TsgcRTCWebSocketDisconnectEvent` | [TsgcRTCWebSocketDisconnectEvent](../types/TsgcRTCWebSocketDisconnectEvent.md) | `__property TsgcRTCWebSocketDisconnectEvent OnRTCWebSocketDisconnect;` |
| `OnRTCWebSocketRemoteDisconnect: TsgcRTCWebSocketRemoteDisconnectEvent` | [TsgcRTCWebSocketRemoteDisconnectEvent](../types/TsgcRTCWebSocketRemoteDisconnectEvent.md) | `__property TsgcRTCWebSocketRemoteDisconnectEvent OnRTCWebSocketRemoteDisconnect;` |
| `OnRTCWebSocketMessage: TsgcRTCWebSocketMessageEvent` | [TsgcRTCWebSocketMessageEvent](../types/TsgcRTCWebSocketMessageEvent.md) | `__property TsgcRTCWebSocketMessageEvent OnRTCWebSocketMessage;` |
| `OnRTCLocalCandidate: TsgcRTCLocalCandidateEvent` | [TsgcRTCLocalCandidateEvent](../types/TsgcRTCLocalCandidateEvent.md) | `__property TsgcRTCLocalCandidateEvent OnRTCLocalCandidate;` |
| `OnRTCLocalDescription: TsgcRTCLocalDescriptionEvent` | [TsgcRTCLocalDescriptionEvent](../types/TsgcRTCLocalDescriptionEvent.md) | `__property TsgcRTCLocalDescriptionEvent OnRTCLocalDescription;` |
| `OnRTCRemoteCandidate: TsgcRTCRemoteCandidateEvent` | [TsgcRTCRemoteCandidateEvent](../types/TsgcRTCRemoteCandidateEvent.md) | `__property TsgcRTCRemoteCandidateEvent OnRTCRemoteCandidate;` |
| `OnRTCRemoteDescription: TsgcRTCRemoteDescriptionEvent` | [TsgcRTCRemoteDescriptionEvent](../types/TsgcRTCRemoteDescriptionEvent.md) | `__property TsgcRTCRemoteDescriptionEvent OnRTCRemoteDescription;` |
| `OnRTCCandidatePairNominated: TsgcRTCCandidatePairNominatedEvent` | [TsgcRTCCandidatePairNominatedEvent](../types/TsgcRTCCandidatePairNominatedEvent.md) | `__property TsgcRTCCandidatePairNominatedEvent OnRTCCandidatePairNominated;` |
| `OnRTCCandidatePairFailed: TsgcRTCCandidatePairFailedEvent` | [TsgcRTCCandidatePairFailedEvent](../types/TsgcRTCCandidatePairFailedEvent.md) | `__property TsgcRTCCandidatePairFailedEvent OnRTCCandidatePairFailed;` |
| `OnRTCConnect: TsgcRTCConnectEvent` | [TsgcRTCConnectEvent](../types/TsgcRTCConnectEvent.md) | `__property TsgcRTCConnectEvent OnRTCConnect;` |
| `OnRTCMessage: TsgcRTCMessageEvent` | [TsgcRTCMessageEvent](../types/TsgcRTCMessageEvent.md) | `__property TsgcRTCMessageEvent OnRTCMessage;` |
| `OnRTCException: TsgcRTCExceptionEvent` | [TsgcRTCExceptionEvent](../types/TsgcRTCExceptionEvent.md) | `__property TsgcRTCExceptionEvent OnRTCException;` |

## Methods

Delphi

```pascal
procedure Clear;
procedure GatherCandidates;
procedure WriteData(const aText: string);
```

C++Builder

```cpp
void __fastcall Clear();
void __fastcall GatherCandidates();
void __fastcall WriteData(const UnicodeString aText);
```

