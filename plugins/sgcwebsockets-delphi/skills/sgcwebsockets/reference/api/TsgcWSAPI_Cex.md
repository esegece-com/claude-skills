# TsgcWSAPI_Cex

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Cex: TsgcWSCex_Options` | [TsgcWSCex_Options](../types/TsgcWSCex_Options.md) | `__property TsgcWSCex_Options * Cex;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnCexConnect: TsgcWSCexConnectEvent` | [TsgcWSCexConnectEvent](../types/TsgcWSCexConnectEvent.md) | `__property TsgcWSCexConnectEvent OnCexConnect;` |
| `OnCexSubscribed: TsgcWSCexSubscribedEvent` | [TsgcWSCexSubscribedEvent](../types/TsgcWSCexSubscribedEvent.md) | `__property TsgcWSCexSubscribedEvent OnCexSubscribed;` |
| `OnCexMessage: TsgcWSCexMessageEvent` | [TsgcWSCexMessageEvent](../types/TsgcWSCexMessageEvent.md) | `__property TsgcWSCexMessageEvent OnCexMessage;` |
| `OnCexAuthenticated: TsgcWSCexAuthenticatedEvent` | [TsgcWSCexAuthenticatedEvent](../types/TsgcWSCexAuthenticatedEvent.md) | `__property TsgcWSCexAuthenticatedEvent OnCexAuthenticated;` |
| `OnCexError: TsgcWSCexErrorEvent` | [TsgcWSCexErrorEvent](../types/TsgcWSCexErrorEvent.md) | `__property TsgcWSCexErrorEvent OnCexError;` |
| `OnCexDisconnecting: TsgcWSCexDisconnectingEvent` | [TsgcWSCexDisconnectingEvent](../types/TsgcWSCexDisconnectingEvent.md) | `__property TsgcWSCexDisconnectingEvent OnCexDisconnecting;` |
| `OnCexDisconnect: TsgcWSCexDisconnectEvent` | [TsgcWSCexDisconnectEvent](../types/TsgcWSCexDisconnectEvent.md) | `__property TsgcWSCexDisconnectEvent OnCexDisconnect;` |
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
procedure Authenticate;
procedure SubscribeTickers;
procedure UnSubscribeTickers;
procedure SubscribePair(const aSymbolPair1, aSymbolPair2: String);
procedure UnSubscribePair(const aSymbolPair1, aSymbolPair2: String);
procedure SubscribeChart(aPeriod: TsgcWSCexPeriods; const aSymbolPair1, aSymbolPair2: String);
procedure GetTicker(const aSymbolPair1, aSymbolPair2: String);
procedure GetBalance;
procedure SubscribeOrderBook(const aSymbolPair1, aSymbolPair2: String; aSubscribe: Boolean = True; const aDepth: Integer = -1);
procedure UnSubscribeOrderBook(const aSymbolPair1, aSymbolPair2: String);
procedure GetOpenOrders(const aSymbolPair1, aSymbolPair2: String);
procedure PlaceOrder(const aSymbolPair1, aSymbolPair2: String; aAmount, aPrice: Currency; aType: TsgcWSCexOrderType);
procedure CancelReplaceOrder(const aOrderId, aSymbolPair1, aSymbolPair2: String; aAmount, aPrice: Currency; aType: TsgcWSCexOrderType);
procedure GetOrderRequest(const aOrderId: String);
procedure CancelOrderRequest(const aOrderId: String);
procedure GetArchivedOrders(const aSymbolPair1, aSymbolPair2: String; const aLimit: Integer = 10);
procedure OpenPosition(const aSymbolPair1, aSymbolPair2, aSymbol: String; aAmount, aLeverage: Integer; aAnySlippage: Boolean; aEOPrice, aStopLossPrice: Currency);
procedure GetPosition(const aId: String);
procedure GetOpenPositions(const aSymbolPair1, aSymbolPair2: String);
procedure ClosePosition(const aId, aSymbolPair1, aSymbolPair2: String);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall Authenticate();
void __fastcall SubscribeTickers();
void __fastcall UnSubscribeTickers();
void __fastcall SubscribePair(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall UnSubscribePair(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall SubscribeChart(TsgcWSCexPeriods * aPeriod, const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall GetTicker(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall GetBalance();
void __fastcall SubscribeOrderBook(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2, bool aSubscribe = True, const int aDepth = -1);
void __fastcall UnSubscribeOrderBook(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall GetOpenOrders(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall PlaceOrder(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2, System::Currency aAmount, System::Currency aPrice, TsgcWSCexOrderType * aType);
void __fastcall CancelReplaceOrder(const UnicodeString aOrderId, const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2, System::Currency aAmount, System::Currency aPrice, TsgcWSCexOrderType * aType);
void __fastcall GetOrderRequest(const UnicodeString aOrderId);
void __fastcall CancelOrderRequest(const UnicodeString aOrderId);
void __fastcall GetArchivedOrders(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2, const int aLimit = 10);
void __fastcall OpenPosition(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2, const UnicodeString aSymbol, int aAmount, int aLeverage, bool aAnySlippage, System::Currency aEOPrice, System::Currency aStopLossPrice);
void __fastcall GetPosition(const UnicodeString aId);
void __fastcall GetOpenPositions(const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall ClosePosition(const UnicodeString aId, const UnicodeString aSymbolPair1, const UnicodeString aSymbolPair2);
void __fastcall QueueClear();
```

