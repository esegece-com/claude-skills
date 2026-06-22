# TsgcWSAPI_Forex

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Credentials: TsgcWSForexCredentials` | [TsgcWSForexCredentials](../types/TsgcWSForexCredentials.md) | `__property TsgcWSForexCredentials * Credentials;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Forex` | [TsgcHTTP_API_Forex](../types/TsgcHTTP_API_Forex.md) | `__property TsgcHTTP_API_Forex * REST_API;` |
| `SessionToken: string (read-only)` | `string` | `__property UnicodeString SessionToken /* read-only */;` |
| `ClientAccountId: Int64` | `Int64` | `__property long long ClientAccountId;` |
| `TradingAccountId: Int64` | `Int64` | `__property long long TradingAccountId;` |
| `AutoReconnect: Boolean` | `Boolean` | `__property bool AutoReconnect;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnForexConnect: TsgcWSForexConnectEvent` | [TsgcWSForexConnectEvent](../types/TsgcWSForexConnectEvent.md) | `__property TsgcWSForexConnectEvent OnForexConnect;` |
| `OnForexDisconnect: TsgcWSForexDisconnectEvent` | [TsgcWSForexDisconnectEvent](../types/TsgcWSForexDisconnectEvent.md) | `__property TsgcWSForexDisconnectEvent OnForexDisconnect;` |
| `OnForexException: TsgcWSForexExceptionEvent` | [TsgcWSForexExceptionEvent](../types/TsgcWSForexExceptionEvent.md) | `__property TsgcWSForexExceptionEvent OnForexException;` |
| `OnForexPriceTick: TsgcWSForexPriceTickEvent` | [TsgcWSForexPriceTickEvent](../types/TsgcWSForexPriceTickEvent.md) | `__property TsgcWSForexPriceTickEvent OnForexPriceTick;` |
| `OnForexOrderUpdate: TsgcWSForexOrderUpdateEvent` | [TsgcWSForexOrderUpdateEvent](../types/TsgcWSForexOrderUpdateEvent.md) | `__property TsgcWSForexOrderUpdateEvent OnForexOrderUpdate;` |
| `OnForexPositionUpdate: TsgcWSForexPositionUpdateEvent` | [TsgcWSForexPositionUpdateEvent](../types/TsgcWSForexPositionUpdateEvent.md) | `__property TsgcWSForexPositionUpdateEvent OnForexPositionUpdate;` |
| `OnForexAccountMargin: TsgcWSForexMarginEvent` | [TsgcWSForexMarginEvent](../types/TsgcWSForexMarginEvent.md) | `__property TsgcWSForexMarginEvent OnForexAccountMargin;` |
| `OnForexQuote: TsgcWSForexQuoteEvent` | [TsgcWSForexQuoteEvent](../types/TsgcWSForexQuoteEvent.md) | `__property TsgcWSForexQuoteEvent OnForexQuote;` |
| `OnForexSubscribe: TsgcWSForexSubscribeEvent` | [TsgcWSForexSubscribeEvent](../types/TsgcWSForexSubscribeEvent.md) | `__property TsgcWSForexSubscribeEvent OnForexSubscribe;` |
| `OnForexUnsubscribe: TsgcWSForexUnsubscribeEvent` | [TsgcWSForexUnsubscribeEvent](../types/TsgcWSForexUnsubscribeEvent.md) | `__property TsgcWSForexUnsubscribeEvent OnForexUnsubscribe;` |
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
procedure Connect;
procedure Disconnect;
function NewTradeOrder(const aMarketId, aTradingAccountId: Int64; const aDirection: string; const aQuantity: Double; const aBidPrice, aOfferPrice: Double; const aAuditId: string) : string;
function UpdateTradeOrder(const aOrder: TsgcHTTPForexTradeOrder): string;
function NewStopLimitOrder(const aOrder : TsgcHTTPForexStopLimitOrder): string;
function UpdateStopLimitOrder(const aOrder : TsgcHTTPForexStopLimitOrder): string;
function CancelOrder(const aOrderId, aTradingAccountId, aMarketId: Int64) : string;
procedure WatchMarket(const aMarketId: Int64);
procedure UnwatchMarket(const aMarketId: Int64);
function IsWatching(const aMarketId: Int64): Boolean;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Connect();
void __fastcall Disconnect();
UnicodeString __fastcall NewTradeOrder(const long long aMarketId, const long long aTradingAccountId, const UnicodeString aDirection, const double aQuantity, const double aBidPrice, const double aOfferPrice, const UnicodeString aAuditId);
UnicodeString __fastcall UpdateTradeOrder(const TsgcHTTPForexTradeOrder * aOrder);
UnicodeString __fastcall NewStopLimitOrder(const TsgcHTTPForexStopLimitOrder * aOrder);
UnicodeString __fastcall UpdateStopLimitOrder(const TsgcHTTPForexStopLimitOrder * aOrder);
UnicodeString __fastcall CancelOrder(const long long aOrderId, const long long aTradingAccountId, const long long aMarketId);
void __fastcall WatchMarket(const long long aMarketId);
void __fastcall UnwatchMarket(const long long aMarketId);
bool __fastcall IsWatching(const long long aMarketId);
void __fastcall QueueClear();
```

