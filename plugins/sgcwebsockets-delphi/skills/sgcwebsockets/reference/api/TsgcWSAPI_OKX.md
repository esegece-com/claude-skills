# TsgcWSAPI_OKX

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `OKX: TsgcWSOKX_Options` | [TsgcWSOKX_Options](../types/TsgcWSOKX_Options.md) | `__property TsgcWSOKX_Options * OKX;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnOKXConnect: TsgcWSOKXConnectEvent` | [TsgcWSOKXConnectEvent](../types/TsgcWSOKXConnectEvent.md) | `__property TsgcWSOKXConnectEvent OnOKXConnect;` |
| `OnOKXSubscribed: TsgcWSOKXSubscribedEvent` | [TsgcWSOKXSubscribedEvent](../types/TsgcWSOKXSubscribedEvent.md) | `__property TsgcWSOKXSubscribedEvent OnOKXSubscribed;` |
| `OnOKXUnsubscribed: TsgcWSOKXUnsubscribedEvent` | [TsgcWSOKXUnsubscribedEvent](../types/TsgcWSOKXUnsubscribedEvent.md) | `__property TsgcWSOKXUnsubscribedEvent OnOKXUnsubscribed;` |
| `OnOKXMessage: TsgcWSOKXMessageEvent` | [TsgcWSOKXMessageEvent](../types/TsgcWSOKXMessageEvent.md) | `__property TsgcWSOKXMessageEvent OnOKXMessage;` |
| `OnOKXError: TsgcWSOKXErrorEvent` | [TsgcWSOKXErrorEvent](../types/TsgcWSOKXErrorEvent.md) | `__property TsgcWSOKXErrorEvent OnOKXError;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure SubscribeInstruments(aInstType : TsgcWSOKXInstrumentTypes = okxitSpot);
procedure UnSubscribeInstruments(aInstType : TsgcWSOKXInstrumentTypes = okxitSpot);
procedure SubscribeTicker(const aInstId: string);
procedure UnSubscribeTicker(const aInstId: string);
procedure SubscribeOpenInterest(const aInstId: string);
procedure UnSubscribeOpenInterest(const aInstId: string);
procedure SubscribeCandlestick(const aInstId: string; aCandlestick: TsgcWSOKXCandlesticks = okxCandle5m);
procedure UnSubscribeCandlestick(const aInstId: string; aCandlestick: TsgcWSOKXCandlesticks = okxCandle5m);
procedure SubscribeTrades(const aInstId: string);
procedure UnSubscribeTrades(const aInstId: string);
procedure SubscribeEstimatedPrices(aInstType : TsgcWSOKXInstrumentTypes = okxitFutures; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribeEstimatedPrices(aInstType : TsgcWSOKXInstrumentTypes = okxitFutures; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeMarkPrice(const aInstId: string);
procedure UnSubscribeMarkPrice(const aInstId: string);
procedure SubscribeMarkPriceCandlestick(const aInstId: string; aMarkPriceCandlestick: TsgcWSOKXMarkPriceCandlesticks = okxMarkPriceCandle5m);
procedure UnSubscribeMarkPriceCandlestick(const aInstId: string; aMarkPriceCandlestick: TsgcWSOKXMarkPriceCandlesticks = okxMarkPriceCandle5m);
procedure SubscribePriceLimit(const aInstId: string);
procedure UnSubscribePriceLimit(const aInstId: string);
procedure SubscribeOrderBook(const aInstId: string; aOrderBook: TsgcWSOKXOrderBook = okxobBooks);
procedure UnSubscribeOrderBook(const aInstId: string; aOrderBook: TsgcWSOKXOrderBook = okxobBooks);
procedure SubscribeOptionSummary(const aUnderlying: string);
procedure UnSubscribeOptionSummary(const aUnderlying: string);
procedure SubscribeFundingRate(const aInstId: string);
procedure UnSubscribeFundingRate(const aInstId: string);
procedure SubscribeIndexCandlestick(const aInstId: string; aIndexCandlestick: TsgcWSOKXIndexCandlesticks = okxIndexCandle5m);
procedure UnSubscribeIndexCandlestick(const aInstId: string; aIndexCandlestick: TsgcWSOKXIndexCandlesticks = okxIndexCandle5m);
procedure SubscribeIndexTicker(const aInstId: string);
procedure UnSubscribeIndexTicker(const aInstId: string);
procedure SubscribeStatus;
procedure UnSubscribeStatus;
procedure SubscribePublicStructureBlockTrades;
procedure UnSubscribePublicStructureBlockTrades;
procedure SubscribeBlockTickers(const aInstId: string);
procedure UnSubscribeBlockTickers(const aInstId: string);
procedure SubscribeAccount(const aCurrency: string = '');
procedure UnSubscribeAccount(const aCurrency: string = '');
procedure SubscribePositions(aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribePositions(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeBalanceAndPosition;
procedure UnSubscribeBalanceAndPosition;
procedure SubscribeOrders(aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribeOrders(aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeOrdersAlgo(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribeOrdersAlgo(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeAdvanceAlgo(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribeAdvanceAlgo(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribePositionRisk(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribePositionRisk(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeAccountGreeks(const aCurrency: string = '');
procedure UnSubscribeAccountGreeks(const aCurrency: string = '');
procedure SubscribeRfqs;
procedure UnSubscribeRfqs;
procedure SubscribeQuotes;
procedure UnSubscribeQuotes;
procedure SubscribePrivateStructureBlockTrades;
procedure UnSubscribePrivateStructureBlockTrades;
procedure SubscribeSpotGridAlgoOrders (aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = ''; const aAlgoId: string = '');
procedure UnSubscribeSpotGridAlgoOrders (aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = ''; const aAlgoId: string = '');
procedure SubscribeContactGridAlgoOrders (aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = ''; const aAlgoId: string = '');
procedure UnSubscribeContactGridAlgoOrders (aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = ''; const aAlgoId: string = '');
procedure SubscribeGridPositions(const aAlgoId: string);
procedure UnSubscribeGridPositions(const aAlgoId: string);
procedure SubscribeGridSubOrders(const aAlgoId: string);
procedure UnSubscribeGridSubOrders(const aAlgoId: string);
procedure SubscribeAllTrades(const aInstId: string);
procedure UnSubscribeAllTrades(const aInstId: string);
procedure SubscribeLiquidationOrders(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = '');
procedure UnSubscribeLiquidationOrders(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = '');
procedure SubscribeADLWarning(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure UnSubscribeADLWarning(aInstType : TsgcWSOKXInstrumentTypes = okxitAny; const aUnderlying: string = ''; const aInstId: string = '');
procedure SubscribeEconomicCalendar;
procedure UnSubscribeEconomicCalendar;
procedure SubscribePublicBlockTrades;
procedure UnSubscribePublicBlockTrades;
procedure SubscribeOptionTrades(const aInstId: string = ''; const aInstFamily: string = '');
procedure UnSubscribeOptionTrades(const aInstId: string = ''; const aInstFamily: string = '');
procedure SubscribeCallAuctionDetails(const aInstId: string);
procedure UnSubscribeCallAuctionDetails(const aInstId: string);
procedure SubscribeFills(aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = '');
procedure UnSubscribeFills(aInstType: TsgcWSOKXInstrumentTypes = okxitAny; const aInstId: string = '');
procedure SubscribeDepositInfo;
procedure UnSubscribeDepositInfo;
procedure SubscribeWithdrawalInfo;
procedure UnSubscribeWithdrawalInfo;
function PlaceOrder(const aOrder: TsgcWSOKX_Order): string;
function PlaceMarketOrder(const aSide: TsgcWSOKXOrderSide; const aInstId: string; const aSize: Double; aTdMode: TsgcWSOKXTradeMode = okxtmDefault): string;
function PlaceLimitOrder(const aSide: TsgcWSOKXOrderSide; const aInstId: string; aSize, aPrice: Double; aTdMode: TsgcWSOKXTradeMode = okxtmDefault): string;
function CancelOrder(const aInstId: string; const aOrdId: string = ''; const aClOrdId: string = ''): string;
function AmendOrder(const aInstId: string; const aOrdId: string = ''; const aClOrdId: string = ''; aNewSize: Double = 0; aNewPrice: Double = 0; aCxlOnFail: Boolean = False): string;
function BatchPlaceOrders(const aOrders: string): string;
function BatchCancelOrders(const aOrders: string): string;
function BatchAmendOrders(const aOrders: string): string;
function MassCancelOrders(const aInstType: string; const aInstFamily: string): string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeInstruments(TsgcWSOKXInstrumentTypes * aInstType = okxitSpot);
void __fastcall UnSubscribeInstruments(TsgcWSOKXInstrumentTypes * aInstType = okxitSpot);
void __fastcall SubscribeTicker(const UnicodeString aInstId);
void __fastcall UnSubscribeTicker(const UnicodeString aInstId);
void __fastcall SubscribeOpenInterest(const UnicodeString aInstId);
void __fastcall UnSubscribeOpenInterest(const UnicodeString aInstId);
void __fastcall SubscribeCandlestick(const UnicodeString aInstId, TsgcWSOKXCandlesticks * aCandlestick = okxCandle5m);
void __fastcall UnSubscribeCandlestick(const UnicodeString aInstId, TsgcWSOKXCandlesticks * aCandlestick = okxCandle5m);
void __fastcall SubscribeTrades(const UnicodeString aInstId);
void __fastcall UnSubscribeTrades(const UnicodeString aInstId);
void __fastcall SubscribeEstimatedPrices(TsgcWSOKXInstrumentTypes * aInstType = okxitFutures, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribeEstimatedPrices(TsgcWSOKXInstrumentTypes * aInstType = okxitFutures, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeMarkPrice(const UnicodeString aInstId);
void __fastcall UnSubscribeMarkPrice(const UnicodeString aInstId);
void __fastcall SubscribeMarkPriceCandlestick(const UnicodeString aInstId, TsgcWSOKXMarkPriceCandlesticks * aMarkPriceCandlestick = okxMarkPriceCandle5m);
void __fastcall UnSubscribeMarkPriceCandlestick(const UnicodeString aInstId, TsgcWSOKXMarkPriceCandlesticks * aMarkPriceCandlestick = okxMarkPriceCandle5m);
void __fastcall SubscribePriceLimit(const UnicodeString aInstId);
void __fastcall UnSubscribePriceLimit(const UnicodeString aInstId);
void __fastcall SubscribeOrderBook(const UnicodeString aInstId, TsgcWSOKXOrderBook * aOrderBook = okxobBooks);
void __fastcall UnSubscribeOrderBook(const UnicodeString aInstId, TsgcWSOKXOrderBook * aOrderBook = okxobBooks);
void __fastcall SubscribeOptionSummary(const UnicodeString aUnderlying);
void __fastcall UnSubscribeOptionSummary(const UnicodeString aUnderlying);
void __fastcall SubscribeFundingRate(const UnicodeString aInstId);
void __fastcall UnSubscribeFundingRate(const UnicodeString aInstId);
void __fastcall SubscribeIndexCandlestick(const UnicodeString aInstId, TsgcWSOKXIndexCandlesticks * aIndexCandlestick = okxIndexCandle5m);
void __fastcall UnSubscribeIndexCandlestick(const UnicodeString aInstId, TsgcWSOKXIndexCandlesticks * aIndexCandlestick = okxIndexCandle5m);
void __fastcall SubscribeIndexTicker(const UnicodeString aInstId);
void __fastcall UnSubscribeIndexTicker(const UnicodeString aInstId);
void __fastcall SubscribeStatus();
void __fastcall UnSubscribeStatus();
void __fastcall SubscribePublicStructureBlockTrades();
void __fastcall UnSubscribePublicStructureBlockTrades();
void __fastcall SubscribeBlockTickers(const UnicodeString aInstId);
void __fastcall UnSubscribeBlockTickers(const UnicodeString aInstId);
void __fastcall SubscribeAccount(const UnicodeString aCurrency = '');
void __fastcall UnSubscribeAccount(const UnicodeString aCurrency = '');
void __fastcall SubscribePositions(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribePositions(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeBalanceAndPosition();
void __fastcall UnSubscribeBalanceAndPosition();
void __fastcall SubscribeOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribeOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeOrdersAlgo(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribeOrdersAlgo(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeAdvanceAlgo(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribeAdvanceAlgo(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribePositionRisk(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribePositionRisk(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeAccountGreeks(const UnicodeString aCurrency = '');
void __fastcall UnSubscribeAccountGreeks(const UnicodeString aCurrency = '');
void __fastcall SubscribeRfqs();
void __fastcall UnSubscribeRfqs();
void __fastcall SubscribeQuotes();
void __fastcall UnSubscribeQuotes();
void __fastcall SubscribePrivateStructureBlockTrades();
void __fastcall UnSubscribePrivateStructureBlockTrades();
void __fastcall SubscribeSpotGridAlgoOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '', const UnicodeString aAlgoId = '');
void __fastcall UnSubscribeSpotGridAlgoOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '', const UnicodeString aAlgoId = '');
void __fastcall SubscribeContactGridAlgoOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '', const UnicodeString aAlgoId = '');
void __fastcall UnSubscribeContactGridAlgoOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '', const UnicodeString aAlgoId = '');
void __fastcall SubscribeGridPositions(const UnicodeString aAlgoId);
void __fastcall UnSubscribeGridPositions(const UnicodeString aAlgoId);
void __fastcall SubscribeGridSubOrders(const UnicodeString aAlgoId);
void __fastcall UnSubscribeGridSubOrders(const UnicodeString aAlgoId);
void __fastcall SubscribeAllTrades(const UnicodeString aInstId);
void __fastcall UnSubscribeAllTrades(const UnicodeString aInstId);
void __fastcall SubscribeLiquidationOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '');
void __fastcall UnSubscribeLiquidationOrders(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '');
void __fastcall SubscribeADLWarning(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall UnSubscribeADLWarning(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aUnderlying = '', const UnicodeString aInstId = '');
void __fastcall SubscribeEconomicCalendar();
void __fastcall UnSubscribeEconomicCalendar();
void __fastcall SubscribePublicBlockTrades();
void __fastcall UnSubscribePublicBlockTrades();
void __fastcall SubscribeOptionTrades(const UnicodeString aInstId = '', const UnicodeString aInstFamily = '');
void __fastcall UnSubscribeOptionTrades(const UnicodeString aInstId = '', const UnicodeString aInstFamily = '');
void __fastcall SubscribeCallAuctionDetails(const UnicodeString aInstId);
void __fastcall UnSubscribeCallAuctionDetails(const UnicodeString aInstId);
void __fastcall SubscribeFills(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '');
void __fastcall UnSubscribeFills(TsgcWSOKXInstrumentTypes * aInstType = okxitAny, const UnicodeString aInstId = '');
void __fastcall SubscribeDepositInfo();
void __fastcall UnSubscribeDepositInfo();
void __fastcall SubscribeWithdrawalInfo();
void __fastcall UnSubscribeWithdrawalInfo();
UnicodeString __fastcall PlaceOrder(const TsgcWSOKX_Order * aOrder);
UnicodeString __fastcall PlaceMarketOrder(const TsgcWSOKXOrderSide * aSide, const UnicodeString aInstId, const double aSize, TsgcWSOKXTradeMode * aTdMode = okxtmDefault);
UnicodeString __fastcall PlaceLimitOrder(const TsgcWSOKXOrderSide * aSide, const UnicodeString aInstId, double aSize, double aPrice, TsgcWSOKXTradeMode * aTdMode = okxtmDefault);
UnicodeString __fastcall CancelOrder(const UnicodeString aInstId, const UnicodeString aOrdId = '', const UnicodeString aClOrdId = '');
UnicodeString __fastcall AmendOrder(const UnicodeString aInstId, const UnicodeString aOrdId = '', const UnicodeString aClOrdId = '', double aNewSize = 0, double aNewPrice = 0, bool aCxlOnFail = False);
UnicodeString __fastcall BatchPlaceOrders(const UnicodeString aOrders);
UnicodeString __fastcall BatchCancelOrders(const UnicodeString aOrders);
UnicodeString __fastcall BatchAmendOrders(const UnicodeString aOrders);
UnicodeString __fastcall MassCancelOrders(const UnicodeString aInstType, const UnicodeString aInstFamily);
void __fastcall QueueClear();
```

