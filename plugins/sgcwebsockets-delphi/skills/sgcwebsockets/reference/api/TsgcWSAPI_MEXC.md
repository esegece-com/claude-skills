# TsgcWSAPI_MEXC

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `MEXCAPI: TsgcWSMEXC_API_Options` | [TsgcWSMEXC_API_Options](../types/TsgcWSMEXC_API_Options.md) | `__property TsgcWSMEXC_API_Options * MEXCAPI;` |
| `MEXCUserDataStreams: TsgcWSMEXC_UserDataStreams_Options` | [TsgcWSMEXC_UserDataStreams_Options](../types/TsgcWSMEXC_UserDataStreams_Options.md) | `__property TsgcWSMEXC_UserDataStreams_Options * MEXCUserDataStreams;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ListenKey: string (read-only)` | `string` | `__property UnicodeString ListenKey /* read-only */;` |
| `REST_API: TsgcHTTP_API_MEXC_Spot` | [TsgcHTTP_API_MEXC_Spot](../types/TsgcHTTP_API_MEXC_Spot.md) | `__property TsgcHTTP_API_MEXC_Spot * REST_API;` |
| `LastPong: TDateTime (read-only)` | `TDateTime` | `__property System::TDateTime LastPong /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnMEXCResponse: TsgcWSMEXCResponseEvent` | [TsgcWSMEXCResponseEvent](../types/TsgcWSMEXCResponseEvent.md) | `__property TsgcWSMEXCResponseEvent OnMEXCResponse;` |
| `OnMEXCMarketStream: TsgcWSMEXCMarketStreamEvent` | [TsgcWSMEXCMarketStreamEvent](../types/TsgcWSMEXCMarketStreamEvent.md) | `__property TsgcWSMEXCMarketStreamEvent OnMEXCMarketStream;` |
| `OnMEXCUserDataStream: TsgcWSMEXCUserDataStreamEvent` | [TsgcWSMEXCUserDataStreamEvent](../types/TsgcWSMEXCUserDataStreamEvent.md) | `__property TsgcWSMEXCUserDataStreamEvent OnMEXCUserDataStream;` |
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
procedure SubscribeTrade(const aSymbol: string; aInterval: Integer = 100);
procedure UnSubscribeTrade(const aSymbol: string; aInterval: Integer = 100);
procedure SubscribeKline(const aSymbol: string; aInterval: TsgcWSMEXCKlineInterval = mexcKlineMin15);
procedure UnSubscribeKline(const aSymbol: string; aInterval: TsgcWSMEXCKlineInterval = mexcKlineMin15);
procedure SubscribeDiffDepth(const aSymbol: string; aInterval: Integer = 100);
procedure UnSubscribeDiffDepth(const aSymbol: string; aInterval: Integer = 100);
procedure SubscribeBookDepth(const aSymbol: string; aInterval: Integer = 5);
procedure UnSubscribeBookDepth(const aSymbol: string; aInterval: Integer = 5);
procedure SubscribeBookTicker(const aSymbol: string; aInterval: Integer = 100);
procedure UnSubscribeBookTicker(const aSymbol: string; aInterval: Integer = 100);
procedure SubscribeBookTickerBatch(const aSymbol: string);
procedure UnSubscribeBookTickerBatch(const aSymbol: string);
procedure SubscribeMiniTickers(const aUTC: string);
procedure UnSubscribeMiniTickers(const aUTC: string);
procedure SubscribeMiniTicker(const aSymbol, aUTC: string);
procedure UnSubscribeMiniTicker(const aSymbol, aUTC: string);
procedure SubscribeAccountUpdate;
procedure UnSubscribeAccountUpdate;
procedure SubscribeAccountDeals;
procedure UnSubscribeAccountDeals;
procedure SubscribeAccountOrders;
procedure UnSubscribeAccountOrders;
procedure Ping;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeTrade(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall UnSubscribeTrade(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall SubscribeKline(const UnicodeString aSymbol, TsgcWSMEXCKlineInterval * aInterval = mexcKlineMin15);
void __fastcall UnSubscribeKline(const UnicodeString aSymbol, TsgcWSMEXCKlineInterval * aInterval = mexcKlineMin15);
void __fastcall SubscribeDiffDepth(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall UnSubscribeDiffDepth(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall SubscribeBookDepth(const UnicodeString aSymbol, int aInterval = 5);
void __fastcall UnSubscribeBookDepth(const UnicodeString aSymbol, int aInterval = 5);
void __fastcall SubscribeBookTicker(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall UnSubscribeBookTicker(const UnicodeString aSymbol, int aInterval = 100);
void __fastcall SubscribeBookTickerBatch(const UnicodeString aSymbol);
void __fastcall UnSubscribeBookTickerBatch(const UnicodeString aSymbol);
void __fastcall SubscribeMiniTickers(const UnicodeString aUTC);
void __fastcall UnSubscribeMiniTickers(const UnicodeString aUTC);
void __fastcall SubscribeMiniTicker(const UnicodeString aSymbol, const UnicodeString aUTC);
void __fastcall UnSubscribeMiniTicker(const UnicodeString aSymbol, const UnicodeString aUTC);
void __fastcall SubscribeAccountUpdate();
void __fastcall UnSubscribeAccountUpdate();
void __fastcall SubscribeAccountDeals();
void __fastcall UnSubscribeAccountDeals();
void __fastcall SubscribeAccountOrders();
void __fastcall UnSubscribeAccountOrders();
void __fastcall Ping();
void __fastcall QueueClear();
```

