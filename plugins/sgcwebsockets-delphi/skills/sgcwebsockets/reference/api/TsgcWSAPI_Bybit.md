# TsgcWSAPI_Bybit

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Bybit: TsgcWSBybit_Options` | [TsgcWSBybit_Options](../types/TsgcWSBybit_Options.md) | `__property TsgcWSBybit_Options * Bybit;` |
| `BybitClient: TsgcWSBybitClient` | [TsgcWSBybitClient](../types/TsgcWSBybitClient.md) | `__property TsgcWSBybitClient * BybitClient;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Bybit` | [TsgcHTTP_API_Bybit](../types/TsgcHTTP_API_Bybit.md) | `__property TsgcHTTP_API_Bybit * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnBybitAuthentication: TsgcWSBybitAuthenticationEvent` | [TsgcWSBybitAuthenticationEvent](../types/TsgcWSBybitAuthenticationEvent.md) | `__property TsgcWSBybitAuthenticationEvent OnBybitAuthentication;` |
| `OnBybitSubscribe: TsgcWSBybitSubscribeEvent` | [TsgcWSBybitSubscribeEvent](../types/TsgcWSBybitSubscribeEvent.md) | `__property TsgcWSBybitSubscribeEvent OnBybitSubscribe;` |
| `OnBybitUnSubscribe: TsgcWSBybitUnSubscribeEvent` | [TsgcWSBybitUnSubscribeEvent](../types/TsgcWSBybitUnSubscribeEvent.md) | `__property TsgcWSBybitUnSubscribeEvent OnBybitUnSubscribe;` |
| `OnBybitData: TsgcWSBybitDataEvent` | [TsgcWSBybitDataEvent](../types/TsgcWSBybitDataEvent.md) | `__property TsgcWSBybitDataEvent OnBybitData;` |
| `OnBybitError: TsgcWSBybitErrorEvent` | [TsgcWSBybitErrorEvent](../types/TsgcWSBybitErrorEvent.md) | `__property TsgcWSBybitErrorEvent OnBybitError;` |
| `OnBybitHTTPException: TsgcWSBybitHTTPExceptionEvent` | [TsgcWSBybitHTTPExceptionEvent](../types/TsgcWSBybitHTTPExceptionEvent.md) | `__property TsgcWSBybitHTTPExceptionEvent OnBybitHTTPException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Ping;
procedure Initialize;
function SubscribeOrderBook(const aSymbol: string; aLevel: Integer = 1): string;
function UnSubscribeOrderBook(const aSymbol: string; aLevel: Integer = 1): string;
function SubscribeTrade(const aSymbol: string): string;
function UnSubscribeTrade(const aSymbol: string): string;
function SubscribeTicker(const aSymbol: string): string;
function UnSubscribeTicker(const aSymbol: string): string;
function SubscribeKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval = bbkl5min): string;
function UnSubscribeKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval = bbkl5min): string;
function SubscribeLiquidation(const aSymbol: string): string;
function UnSubscribeLiquidation(const aSymbol: string): string;
function SubscribeLT_KLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval = bbkl5min): string;
function UnSubscribeLT_KLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval = bbkl5min): string;
function SubscribeLT_Ticker(const aSymbol: string): string;
function UnSubscribeLT_Ticker(const aSymbol: string): string;
function SubscribeLT_Nav(const aSymbol: string): string;
function UnSubscribeLT_Nav(const aSymbol: string): string;
function SubscribeInsurance: string;
function UnSubscribeInsurance: string;
function SubscribeOrderPriceLimit(const aSymbol: string): string;
function UnSubscribeOrderPriceLimit(const aSymbol: string): string;
function SubscribeADLAlert(const aSymbol: string): string;
function UnSubscribeADLAlert(const aSymbol: string): string;
function SubscribePosition: string;
function UnSubscribePosition: string;
function SubscribeExecution: string;
function UnSubscribeExecution: string;
function SubscribeOrder: string;
function UnSubscribeOrder: string;
function SubscribeWallet: string;
function UnSubscribeWallet: string;
function SubscribeGreek: string;
function UnSubscribeGreek: string;
function SubscribeDcp: string;
function UnSubscribeDcp: string;
function SubscribeFastExecution: string;
function UnSubscribeFastExecution: string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall Initialize();
UnicodeString __fastcall SubscribeOrderBook(const UnicodeString aSymbol, int aLevel = 1);
UnicodeString __fastcall UnSubscribeOrderBook(const UnicodeString aSymbol, int aLevel = 1);
UnicodeString __fastcall SubscribeTrade(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeTrade(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeTicker(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeTicker(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeKLine(const UnicodeString aSymbol, TsgcBybitKLineInterval * aInterval = bbkl5min);
UnicodeString __fastcall UnSubscribeKLine(const UnicodeString aSymbol, TsgcBybitKLineInterval * aInterval = bbkl5min);
UnicodeString __fastcall SubscribeLiquidation(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeLiquidation(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeLT_KLine(const UnicodeString aSymbol, TsgcBybitKLineInterval * aInterval = bbkl5min);
UnicodeString __fastcall UnSubscribeLT_KLine(const UnicodeString aSymbol, TsgcBybitKLineInterval * aInterval = bbkl5min);
UnicodeString __fastcall SubscribeLT_Ticker(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeLT_Ticker(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeLT_Nav(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeLT_Nav(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeInsurance();
UnicodeString __fastcall UnSubscribeInsurance();
UnicodeString __fastcall SubscribeOrderPriceLimit(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeOrderPriceLimit(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeADLAlert(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeADLAlert(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribePosition();
UnicodeString __fastcall UnSubscribePosition();
UnicodeString __fastcall SubscribeExecution();
UnicodeString __fastcall UnSubscribeExecution();
UnicodeString __fastcall SubscribeOrder();
UnicodeString __fastcall UnSubscribeOrder();
UnicodeString __fastcall SubscribeWallet();
UnicodeString __fastcall UnSubscribeWallet();
UnicodeString __fastcall SubscribeGreek();
UnicodeString __fastcall UnSubscribeGreek();
UnicodeString __fastcall SubscribeDcp();
UnicodeString __fastcall UnSubscribeDcp();
UnicodeString __fastcall SubscribeFastExecution();
UnicodeString __fastcall UnSubscribeFastExecution();
void __fastcall QueueClear();
```

