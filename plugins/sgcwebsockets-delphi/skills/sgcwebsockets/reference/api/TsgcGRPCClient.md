# TsgcGRPCClient

unit: sgcHTTP
Edition: requires SGC_GRPC

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcHTTP2CLient_Base` | [TsgcHTTP2CLient_Base](../types/TsgcHTTP2CLient_Base.md) | `__property TsgcHTTP2CLient_Base * Client;` |
| `ChannelOptions: TsgcGRPCChannelOptions` | [TsgcGRPCChannelOptions](../types/TsgcGRPCChannelOptions.md) | `__property TsgcGRPCChannelOptions * ChannelOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `DefaultMetadata: TsgcGRPCMetadata (read-only)` | [TsgcGRPCMetadata](../types/TsgcGRPCMetadata.md) | `__property TsgcGRPCMetadata * DefaultMetadata /* read-only */;` |
| `Interceptors: TsgcGRPCInterceptorChain (read-only)` | [TsgcGRPCInterceptorChain](../types/TsgcGRPCInterceptorChain.md) | `__property TsgcGRPCInterceptorChain * Interceptors /* read-only */;` |
| `RetryPolicy: TsgcGRPCRetryPolicy (read-only)` | [TsgcGRPCRetryPolicy](../types/TsgcGRPCRetryPolicy.md) | `__property TsgcGRPCRetryPolicy * RetryPolicy /* read-only */;` |
| `ServiceConfig: TsgcGRPCServiceConfig (read-only)` | [TsgcGRPCServiceConfig](../types/TsgcGRPCServiceConfig.md) | `__property TsgcGRPCServiceConfig * ServiceConfig /* read-only */;` |
| `MetricsCollector: TsgcGRPCMetricsCollector (read-only)` | [TsgcGRPCMetricsCollector](../types/TsgcGRPCMetricsCollector.md) | `__property TsgcGRPCMetricsCollector * MetricsCollector /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnGRPCConnect: TsgcGRPCClientConnectEvent` | [TsgcGRPCClientConnectEvent](../types/TsgcGRPCClientConnectEvent.md) | `__property TsgcGRPCClientConnectEvent OnGRPCConnect;` |
| `OnGRPCDisconnect: TsgcGRPCClientDisconnectEvent` | [TsgcGRPCClientDisconnectEvent](../types/TsgcGRPCClientDisconnectEvent.md) | `__property TsgcGRPCClientDisconnectEvent OnGRPCDisconnect;` |
| `OnGRPCResponse: TsgcGRPCClientResponseEvent` | [TsgcGRPCClientResponseEvent](../types/TsgcGRPCClientResponseEvent.md) | `__property TsgcGRPCClientResponseEvent OnGRPCResponse;` |
| `OnGRPCStreamMessage: TsgcGRPCClientStreamMessageEvent` | [TsgcGRPCClientStreamMessageEvent](../types/TsgcGRPCClientStreamMessageEvent.md) | `__property TsgcGRPCClientStreamMessageEvent OnGRPCStreamMessage;` |
| `OnGRPCStreamEnd: TsgcGRPCClientStreamEndEvent` | [TsgcGRPCClientStreamEndEvent](../types/TsgcGRPCClientStreamEndEvent.md) | `__property TsgcGRPCClientStreamEndEvent OnGRPCStreamEnd;` |
| `OnGRPCError: TsgcGRPCClientErrorEvent` | [TsgcGRPCClientErrorEvent](../types/TsgcGRPCClientErrorEvent.md) | `__property TsgcGRPCClientErrorEvent OnGRPCError;` |
| `OnGRPCException: TsgcGRPCClientExceptionEvent` | [TsgcGRPCClientExceptionEvent](../types/TsgcGRPCClientExceptionEvent.md) | `__property TsgcGRPCClientExceptionEvent OnGRPCException;` |
| `OnGRPCBeforeRequest: TsgcGRPCClientBeforeRequestEvent` | [TsgcGRPCClientBeforeRequestEvent](../types/TsgcGRPCClientBeforeRequestEvent.md) | `__property TsgcGRPCClientBeforeRequestEvent OnGRPCBeforeRequest;` |

## Methods

Delphi

```pascal
function Call(const aService, aMethod: string; const aRequestData: TBytes; const aCallOptions: TsgcGRPCCallOptions = nil): TsgcGRPCResponse;
procedure CallAsync(const aService, aMethod: string; const aRequestData: TBytes; const aCallOptions: TsgcGRPCCallOptions = nil);
procedure ServerStreamingCall(const aService, aMethod: string; const aRequestData: TBytes; const aCallOptions: TsgcGRPCCallOptions = nil);
function OpenClientStream(const aService, aMethod: string; const aCallOptions: TsgcGRPCCallOptions = nil): Integer;
procedure SendStreamMessage(aStreamId: Integer; const aData: TBytes; aCompress: Boolean = False);
function CloseClientStream(aStreamId: Integer): TsgcGRPCResponse;
procedure CloseClientStreamAsync(aStreamId: Integer);
function OpenBidiStream(const aService, aMethod: string; const aCallOptions: TsgcGRPCCallOptions = nil): Integer;
procedure SendBidiMessage(aStreamId: Integer; const aData: TBytes; aCompress: Boolean = False);
procedure CloseBidiStream(aStreamId: Integer);
procedure CancelCall(aStreamId: Integer);
function CallString(const aService, aMethod: string; const aRequestData: string): string;
```

C++Builder

```cpp
TsgcGRPCResponse * __fastcall Call(const UnicodeString aService, const UnicodeString aMethod, const System::DynamicArray<System::Byte> aRequestData, const TsgcGRPCCallOptions * aCallOptions = nil);
void __fastcall CallAsync(const UnicodeString aService, const UnicodeString aMethod, const System::DynamicArray<System::Byte> aRequestData, const TsgcGRPCCallOptions * aCallOptions = nil);
void __fastcall ServerStreamingCall(const UnicodeString aService, const UnicodeString aMethod, const System::DynamicArray<System::Byte> aRequestData, const TsgcGRPCCallOptions * aCallOptions = nil);
int __fastcall OpenClientStream(const UnicodeString aService, const UnicodeString aMethod, const TsgcGRPCCallOptions * aCallOptions = nil);
void __fastcall SendStreamMessage(int aStreamId, const System::DynamicArray<System::Byte> aData, bool aCompress = False);
TsgcGRPCResponse * __fastcall CloseClientStream(int aStreamId);
void __fastcall CloseClientStreamAsync(int aStreamId);
int __fastcall OpenBidiStream(const UnicodeString aService, const UnicodeString aMethod, const TsgcGRPCCallOptions * aCallOptions = nil);
void __fastcall SendBidiMessage(int aStreamId, const System::DynamicArray<System::Byte> aData, bool aCompress = False);
void __fastcall CloseBidiStream(int aStreamId);
void __fastcall CancelCall(int aStreamId);
UnicodeString __fastcall CallString(const UnicodeString aService, const UnicodeString aMethod, const UnicodeString aRequestData);
```

