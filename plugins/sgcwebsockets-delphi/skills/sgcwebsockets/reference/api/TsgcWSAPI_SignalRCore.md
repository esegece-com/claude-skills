# TsgcWSAPI_SignalRCore

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `SignalRCore: TsgcWSSignalRCore_Options` | [TsgcWSSignalRCore_Options](../types/TsgcWSSignalRCore_Options.md) | `__property TsgcWSSignalRCore_Options * SignalRCore;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSignalRCoreBeforeConnect: TsgcWSSignalRCoreBeforeConnectEvent` | [TsgcWSSignalRCoreBeforeConnectEvent](../types/TsgcWSSignalRCoreBeforeConnectEvent.md) | `__property TsgcWSSignalRCoreBeforeConnectEvent OnSignalRCoreBeforeConnect;` |
| `OnSignalRCoreConnect: TsgcWSSignalRCoreConnectEvent` | [TsgcWSSignalRCoreConnectEvent](../types/TsgcWSSignalRCoreConnectEvent.md) | `__property TsgcWSSignalRCoreConnectEvent OnSignalRCoreConnect;` |
| `OnSignalRCoreInvocation: TsgcWSSignalRCoreInvocationEvent` | [TsgcWSSignalRCoreInvocationEvent](../types/TsgcWSSignalRCoreInvocationEvent.md) | `__property TsgcWSSignalRCoreInvocationEvent OnSignalRCoreInvocation;` |
| `OnSignalRCoreStreamInvocation: TsgcWSSignalRCoreStreamInvocationEvent` | [TsgcWSSignalRCoreStreamInvocationEvent](../types/TsgcWSSignalRCoreStreamInvocationEvent.md) | `__property TsgcWSSignalRCoreStreamInvocationEvent OnSignalRCoreStreamInvocation;` |
| `OnSignalRCoreStreamItem: TsgcWSSignalRCoreStreamItemEvent` | [TsgcWSSignalRCoreStreamItemEvent](../types/TsgcWSSignalRCoreStreamItemEvent.md) | `__property TsgcWSSignalRCoreStreamItemEvent OnSignalRCoreStreamItem;` |
| `OnSignalRCoreCompletion: TsgcWSSignalRCoreCompletionEvent` | [TsgcWSSignalRCoreCompletionEvent](../types/TsgcWSSignalRCoreCompletionEvent.md) | `__property TsgcWSSignalRCoreCompletionEvent OnSignalRCoreCompletion;` |
| `OnSignalRCoreCancelInvocation: TsgcWSSignalRCoreCancelInvocationEvent` | [TsgcWSSignalRCoreCancelInvocationEvent](../types/TsgcWSSignalRCoreCancelInvocationEvent.md) | `__property TsgcWSSignalRCoreCancelInvocationEvent OnSignalRCoreCancelInvocation;` |
| `OnSignalRCoreKeepAlive: TsgcWSSignalRCoreKeepAliveEvent` | [TsgcWSSignalRCoreKeepAliveEvent](../types/TsgcWSSignalRCoreKeepAliveEvent.md) | `__property TsgcWSSignalRCoreKeepAliveEvent OnSignalRCoreKeepAlive;` |
| `OnSignalRCoreError: TsgcWSSignalRCoreErrorEvent` | [TsgcWSSignalRCoreErrorEvent](../types/TsgcWSSignalRCoreErrorEvent.md) | `__property TsgcWSSignalRCoreErrorEvent OnSignalRCoreError;` |
| `OnSignalRCoreClose: TsgcWSSignalRCoreCloseEvent` | [TsgcWSSignalRCoreCloseEvent](../types/TsgcWSSignalRCoreCloseEvent.md) | `__property TsgcWSSignalRCoreCloseEvent OnSignalRCoreClose;` |
| `OnSignalRCoreDisconnect: TsgcWSSignalRCoreDisconnectEvent` | [TsgcWSSignalRCoreDisconnectEvent](../types/TsgcWSSignalRCoreDisconnectEvent.md) | `__property TsgcWSSignalRCoreDisconnectEvent OnSignalRCoreDisconnect;` |
| `OnSignalRCoreMessagePack: TsgcWSSignalRCoreMessagePackEvent` | [TsgcWSSignalRCoreMessagePackEvent](../types/TsgcWSSignalRCoreMessagePackEvent.md) | `__property TsgcWSSignalRCoreMessagePackEvent OnSignalRCoreMessagePack;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure WriteData(const aText: String);
procedure Invoke(const aTarget: String; const aArguments: Array of Const; const aInvocationId: String = '');
function InvokeAndWait(const aTarget: String; aArguments: Array of Const; aInvocationId: String; out Completion: TSignalRCore_Completion; const aTimeout: Integer = 10000): Boolean;
procedure CancelInvocation(const aInvocationId: String);
procedure InvokeStream(const aTarget: String; const aArguments: Array of Const; const aInvocationId: String);
function InvokeStreamAndWait(const aTarget: String; const aArguments: Array of Const; const aInvocationId: String; out Completion: TSignalRCore_Completion; const aTimeout: Integer = 10000): Boolean;
procedure StreamItem(const aInvocationId, aItem: String);
procedure CompletionResult(const aInvocationId, aResult: String);
procedure CompletionError(const aInvocationId, aError: String);
procedure Ping;
procedure Close(const aReason: String = '');
procedure ReConnect(const aConnectionId: String);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText);
void __fastcall Invoke(const UnicodeString aTarget, const Array of Const aArguments, const UnicodeString aInvocationId = '');
bool __fastcall InvokeAndWait(const UnicodeString aTarget, Array of Const aArguments, UnicodeString aInvocationId, TSignalRCore_Completion * &Completion, const int aTimeout = 10000);
void __fastcall CancelInvocation(const UnicodeString aInvocationId);
void __fastcall InvokeStream(const UnicodeString aTarget, const Array of Const aArguments, const UnicodeString aInvocationId);
bool __fastcall InvokeStreamAndWait(const UnicodeString aTarget, const Array of Const aArguments, const UnicodeString aInvocationId, TSignalRCore_Completion * &Completion, const int aTimeout = 10000);
void __fastcall StreamItem(const UnicodeString aInvocationId, const UnicodeString aItem);
void __fastcall CompletionResult(const UnicodeString aInvocationId, const UnicodeString aResult);
void __fastcall CompletionError(const UnicodeString aInvocationId, const UnicodeString aError);
void __fastcall Ping();
void __fastcall Close(const UnicodeString aReason = '');
void __fastcall ReConnect(const UnicodeString aConnectionId);
void __fastcall QueueClear();
```

