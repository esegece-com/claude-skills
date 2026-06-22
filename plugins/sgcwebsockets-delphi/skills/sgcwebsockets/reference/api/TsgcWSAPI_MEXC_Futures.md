# TsgcWSAPI_MEXC_Futures

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `MEXCAPI: TsgcWSMEXC_API_Options` | [TsgcWSMEXC_API_Options](../types/TsgcWSMEXC_API_Options.md) | `__property TsgcWSMEXC_API_Options * MEXCAPI;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_MEXC_Futures` | [TsgcHTTP_API_MEXC_Futures](../types/TsgcHTTP_API_MEXC_Futures.md) | `__property TsgcHTTP_API_MEXC_Futures * REST_API;` |
| `LastPong: TDateTime (read-only)` | `TDateTime` | `__property System::TDateTime LastPong /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnMEXCLogin: TsgcWSMEXFUTCLoginEvent` | [TsgcWSMEXFUTCLoginEvent](../types/TsgcWSMEXFUTCLoginEvent.md) | `__property TsgcWSMEXFUTCLoginEvent OnMEXCLogin;` |
| `OnMEXCSubscribed: TsgcWSMEXCFUTSubscribedEvent` | [TsgcWSMEXCFUTSubscribedEvent](../types/TsgcWSMEXCFUTSubscribedEvent.md) | `__property TsgcWSMEXCFUTSubscribedEvent OnMEXCSubscribed;` |
| `OnMEXCUnsubscribed: TsgcWSMEXCFUTUnsubscribedEvent` | [TsgcWSMEXCFUTUnsubscribedEvent](../types/TsgcWSMEXCFUTUnsubscribedEvent.md) | `__property TsgcWSMEXCFUTUnsubscribedEvent OnMEXCUnsubscribed;` |
| `OnMEXCMessage: TsgcWSMEXCFUTMessageEvent` | [TsgcWSMEXCFUTMessageEvent](../types/TsgcWSMEXCFUTMessageEvent.md) | `__property TsgcWSMEXCFUTMessageEvent OnMEXCMessage;` |
| `OnMEXCError: TsgcWSMEXCFUTErrorEvent` | [TsgcWSMEXCFUTErrorEvent](../types/TsgcWSMEXCFUTErrorEvent.md) | `__property TsgcWSMEXCFUTErrorEvent OnMEXCError;` |
| `OnMEXCException: TsgcWSMEXCExceptionEvent` | [TsgcWSMEXCExceptionEvent](../types/TsgcWSMEXCExceptionEvent.md) | `__property TsgcWSMEXCExceptionEvent OnMEXCException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure SubscribeDeal(const aSymbol: string);
procedure UnSubscribeDeal(const aSymbol: string);
procedure SubscribeTickers;
procedure UnSubscribeTickers;
procedure SubscribeTicker(const aSymbol: string);
procedure UnSubscribeTicker(const aSymbol: string);
procedure SubscribeDepth(const aSymbol: string; aCompress: Boolean = False);
procedure UnSubscribeDepth(const aSymbol: string; aCompress: Boolean = False);
procedure SubscribeDepthFull(const aSymbol: string; aLevel: Integer = 20);
procedure UnSubscribeDepthFull(const aSymbol: string; aLevel: Integer = 20);
procedure SubscribeKline(const aSymbol: string; aInterval: TsgcWSMEXCKlineInterval = mexcKlineMin15);
procedure UnSubscribeKline(const aSymbol: string; aInterval: TsgcWSMEXCKlineInterval = mexcKlineMin15);
procedure SubscribeFundingRate(const aSymbol: string);
procedure UnSubscribeFundingRate(const aSymbol: string);
procedure SubscribeIndexPrice(const aSymbol: string);
procedure UnSubscribeIndexPrice(const aSymbol: string);
procedure SubscribeFairPrice(const aSymbol: string);
procedure UnSubscribeFairPrice(const aSymbol: string);
procedure SubscribePersonalOrder;
procedure UnSubscribePersonalOrder;
procedure SubscribePersonalOrderDeal;
procedure UnSubscribePersonalOrderDeal;
procedure SubscribePersonalPosition;
procedure UnSubscribePersonalPosition;
procedure SubscribePersonalPlanOrder;
procedure UnSubscribePersonalPlanOrder;
procedure SubscribePersonalStopOrder;
procedure UnSubscribePersonalStopOrder;
procedure SubscribePersonalStopPlanOrder;
procedure UnSubscribePersonalStopPlanOrder;
procedure SubscribePersonalRiskLimit;
procedure UnSubscribePersonalRiskLimit;
procedure SubscribePersonalADLLevel;
procedure UnSubscribePersonalADLLevel;
procedure SubscribePersonalAsset;
procedure UnSubscribePersonalAsset;
procedure Ping;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeDeal(const UnicodeString aSymbol);
void __fastcall UnSubscribeDeal(const UnicodeString aSymbol);
void __fastcall SubscribeTickers();
void __fastcall UnSubscribeTickers();
void __fastcall SubscribeTicker(const UnicodeString aSymbol);
void __fastcall UnSubscribeTicker(const UnicodeString aSymbol);
void __fastcall SubscribeDepth(const UnicodeString aSymbol, bool aCompress = False);
void __fastcall UnSubscribeDepth(const UnicodeString aSymbol, bool aCompress = False);
void __fastcall SubscribeDepthFull(const UnicodeString aSymbol, int aLevel = 20);
void __fastcall UnSubscribeDepthFull(const UnicodeString aSymbol, int aLevel = 20);
void __fastcall SubscribeKline(const UnicodeString aSymbol, TsgcWSMEXCKlineInterval * aInterval = mexcKlineMin15);
void __fastcall UnSubscribeKline(const UnicodeString aSymbol, TsgcWSMEXCKlineInterval * aInterval = mexcKlineMin15);
void __fastcall SubscribeFundingRate(const UnicodeString aSymbol);
void __fastcall UnSubscribeFundingRate(const UnicodeString aSymbol);
void __fastcall SubscribeIndexPrice(const UnicodeString aSymbol);
void __fastcall UnSubscribeIndexPrice(const UnicodeString aSymbol);
void __fastcall SubscribeFairPrice(const UnicodeString aSymbol);
void __fastcall UnSubscribeFairPrice(const UnicodeString aSymbol);
void __fastcall SubscribePersonalOrder();
void __fastcall UnSubscribePersonalOrder();
void __fastcall SubscribePersonalOrderDeal();
void __fastcall UnSubscribePersonalOrderDeal();
void __fastcall SubscribePersonalPosition();
void __fastcall UnSubscribePersonalPosition();
void __fastcall SubscribePersonalPlanOrder();
void __fastcall UnSubscribePersonalPlanOrder();
void __fastcall SubscribePersonalStopOrder();
void __fastcall UnSubscribePersonalStopOrder();
void __fastcall SubscribePersonalStopPlanOrder();
void __fastcall UnSubscribePersonalStopPlanOrder();
void __fastcall SubscribePersonalRiskLimit();
void __fastcall UnSubscribePersonalRiskLimit();
void __fastcall SubscribePersonalADLLevel();
void __fastcall UnSubscribePersonalADLLevel();
void __fastcall SubscribePersonalAsset();
void __fastcall UnSubscribePersonalAsset();
void __fastcall Ping();
void __fastcall QueueClear();
```

