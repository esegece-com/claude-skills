# TsgcICEClient

unit: sgcP2P
Edition: Enterprise

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TURNClient: TsgcTURNClient_Base` | [TsgcTURNClient_Base](../types/TsgcTURNClient_Base.md) | `__property TsgcTURNClient_Base * TURNClient;` |
| `ICEOptions: TsgcICEClient_Options` | [TsgcICEClient_Options](../types/TsgcICEClient_Options.md) | `__property TsgcICEClient_Options * ICEOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `LocalDescription: TsgcICE_RTCSessionDescription` | [TsgcICE_RTCSessionDescription](../types/TsgcICE_RTCSessionDescription.md) | `__property TsgcICE_RTCSessionDescription * LocalDescription;` |
| `RemoteDescription: TsgcICE_RTCSessionDescription` | [TsgcICE_RTCSessionDescription](../types/TsgcICE_RTCSessionDescription.md) | `__property TsgcICE_RTCSessionDescription * RemoteDescription;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnICECandidate: TsgcICECandidateEvent` | [TsgcICECandidateEvent](../types/TsgcICECandidateEvent.md) | `__property TsgcICECandidateEvent OnICECandidate;` |
| `OnICECandidateError: TsgcICECandidateErrorEvent` | [TsgcICECandidateErrorEvent](../types/TsgcICECandidateErrorEvent.md) | `__property TsgcICECandidateErrorEvent OnICECandidateError;` |
| `OnICECandidatePairNominated: TsgcICECandidatePairNominatedEvent` | [TsgcICECandidatePairNominatedEvent](../types/TsgcICECandidatePairNominatedEvent.md) | `__property TsgcICECandidatePairNominatedEvent OnICECandidatePairNominated;` |
| `OnICECandidatePairFailed: TsgcICECandidatePairFailedEvent` | [TsgcICECandidatePairFailedEvent](../types/TsgcICECandidatePairFailedEvent.md) | `__property TsgcICECandidatePairFailedEvent OnICECandidatePairFailed;` |
| `OnICEReceiveBindingRequest: TsgcICEReceiveBindingRequestEvent` | [TsgcICEReceiveBindingRequestEvent](../types/TsgcICEReceiveBindingRequestEvent.md) | `__property TsgcICEReceiveBindingRequestEvent OnICEReceiveBindingRequest;` |
| `OnICEException: TsgcICEExceptionEvent` | [TsgcICEExceptionEvent](../types/TsgcICEExceptionEvent.md) | `__property TsgcICEExceptionEvent OnICEException;` |

## Methods

Delphi

```pascal
procedure GatherCandidates;
procedure SetLocalDescription(aType: TsgcICERTCSdpType; const aRTCSessionDescription: string);
procedure SetRemoteDescription(aType: TsgcICERTCSdpType; const aRTCSessionDescription: string);
procedure AddRTCIceCandidate(const aCandidate: string);
procedure ProcessCandidates;
```

C++Builder

```cpp
void __fastcall GatherCandidates();
void __fastcall SetLocalDescription(TsgcICERTCSdpType * aType, const UnicodeString aRTCSessionDescription);
void __fastcall SetRemoteDescription(TsgcICERTCSdpType * aType, const UnicodeString aRTCSessionDescription);
void __fastcall AddRTCIceCandidate(const UnicodeString aCandidate);
void __fastcall ProcessCandidates();
```

