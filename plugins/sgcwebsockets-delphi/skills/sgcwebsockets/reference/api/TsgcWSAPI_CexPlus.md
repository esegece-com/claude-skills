# TsgcWSAPI_CexPlus

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `CexPlus: TsgcWSCexPlus_Options` | [TsgcWSCexPlus_Options](../types/TsgcWSCexPlus_Options.md) | `__property TsgcWSCexPlus_Options * CexPlus;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnCexPlusConnect: TsgcWSCexPlusConnectEvent` | [TsgcWSCexPlusConnectEvent](../types/TsgcWSCexPlusConnectEvent.md) | `__property TsgcWSCexPlusConnectEvent OnCexPlusConnect;` |
| `OnCexPlusSubscribed: TsgcWSCexPlusSubscribedEvent` | [TsgcWSCexPlusSubscribedEvent](../types/TsgcWSCexPlusSubscribedEvent.md) | `__property TsgcWSCexPlusSubscribedEvent OnCexPlusSubscribed;` |
| `OnCexPlusMessage: TsgcWSCexPlusMessageEvent` | [TsgcWSCexPlusMessageEvent](../types/TsgcWSCexPlusMessageEvent.md) | `__property TsgcWSCexPlusMessageEvent OnCexPlusMessage;` |
| `OnCexPlusAuthenticated: TsgcWSCexPlusAuthenticatedEvent` | [TsgcWSCexPlusAuthenticatedEvent](../types/TsgcWSCexPlusAuthenticatedEvent.md) | `__property TsgcWSCexPlusAuthenticatedEvent OnCexPlusAuthenticated;` |
| `OnCexPlusError: TsgcWSCexPlusErrorEvent` | [TsgcWSCexPlusErrorEvent](../types/TsgcWSCexPlusErrorEvent.md) | `__property TsgcWSCexPlusErrorEvent OnCexPlusError;` |
| `OnCexPlusDisconnecting: TsgcWSCexPlusDisconnectingEvent` | [TsgcWSCexPlusDisconnectingEvent](../types/TsgcWSCexPlusDisconnectingEvent.md) | `__property TsgcWSCexPlusDisconnectingEvent OnCexPlusDisconnecting;` |
| `OnCexPlusDisconnect: TsgcWSCexPlusDisconnectEvent` | [TsgcWSCexPlusDisconnectEvent](../types/TsgcWSCexPlusDisconnectEvent.md) | `__property TsgcWSCexPlusDisconnectEvent OnCexPlusDisconnect;` |
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
procedure GetTicker(const aPair: String = '');
procedure GetOrderBook(const aPair: String);
procedure GetCandles(const aPair: string; aDataType: TsgcWSCexPlusDataType; aResolution: TsgcWSCexPlusResolution; aFrom: TDateTime = 0; aTo: TDateTime = 0; aLimit: Integer = 0);
procedure GetTradeHistory(const aPair: string; aSide: TsgcWSCexPlusSide = cxpsUnknown; aFromDateISO: TDateTime = 0; aToDateISO: TDateTime = 0; aFromTradeId: string = ''; aToTradeId: string = ''; aPageSize: Integer = 0);
procedure GetServerTime;
procedure GetPairsInfo(const aPair: String = '');
procedure GetCurrenciesInfo(const aCurrency: string = '');
procedure GetProcessingInfo(const aCurrency: string = '');
procedure SubscribeOrderBook(const aPair: String);
procedure UnSubscribeOrderBook(const aPair: String);
procedure SubscribeTrade(const aPair: String);
procedure UnSubscribeTrade(const aPair: String);
procedure GetCurrentFee(const aPair: String = '');
procedure GetFeeStrategy;
procedure GetVolume;
procedure CreateAccount(const aAccountId, aCurrency: string);
procedure GetAccountStatus;
procedure GetOrders(const aClientOrderId: string = ''; const aOrderId: Int64 = 0; const aPair: string = ''; const aSide: string = '');
procedure NewOrder(const aOrder: TsgcWSCexPlusOrder);
procedure NewMarketOrder(const aCurrency1, aCurrency2: string; aSide: TsgcWSCexPlusSide);
procedure NewLimitOrder(const aCurrency1, aCurrency2: string; aSide: TsgcWSCexPlusSide; aPrice: string);
procedure CancelOrder(const aCancelRequestId: string; const aOrderId: string = ''; const aClientOrderId: string = '');
procedure CancelAllOrders;
procedure GetTransactionHistory(const aAccountId: string = ''; const aType: string = ''; aDateFrom: TDateTime = 0; aDateTo: TDateTime = 0; aSortOrder: string = ''; aPageSize: Integer = 0; aPageNumber: Integer = 0);
procedure GetFundingHistory(const aAccountId: string = ''; aTxId: Int64 = 0; const aDirection: string = ''; const aCurrency: string = ''; aDateFrom: TDateTime = 0; aDateTo: TDateTime = 0; aPageSize: Integer = 0; aPageNumber: Integer = 0);
procedure InternalTransfer(const aFromAccountId, aToAccountId, aCurrency, aAmount: string; const aClientTxId: string = '');
procedure GetDepositAddress(const aAccountId, aCurrency, aBlockChain: string);
procedure FundsDepositFromWallet(const aClientTxId, aAccountId, aCurrency, aAmount: string);
procedure FundsWithdrawalToWallet(const aClientTxId, aAccountId, aCurrency, aAmount: string);
procedure GetWalletBalance;
procedure SubscribeAccountEvents;
procedure UnSubscribeAccountEvents;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall GetTicker(const UnicodeString aPair = '');
void __fastcall GetOrderBook(const UnicodeString aPair);
void __fastcall GetCandles(const UnicodeString aPair, TsgcWSCexPlusDataType * aDataType, TsgcWSCexPlusResolution * aResolution, System::TDateTime aFrom = 0, System::TDateTime aTo = 0, int aLimit = 0);
void __fastcall GetTradeHistory(const UnicodeString aPair, TsgcWSCexPlusSide * aSide = cxpsUnknown, System::TDateTime aFromDateISO = 0, System::TDateTime aToDateISO = 0, UnicodeString aFromTradeId = '', UnicodeString aToTradeId = '', int aPageSize = 0);
void __fastcall GetServerTime();
void __fastcall GetPairsInfo(const UnicodeString aPair = '');
void __fastcall GetCurrenciesInfo(const UnicodeString aCurrency = '');
void __fastcall GetProcessingInfo(const UnicodeString aCurrency = '');
void __fastcall SubscribeOrderBook(const UnicodeString aPair);
void __fastcall UnSubscribeOrderBook(const UnicodeString aPair);
void __fastcall SubscribeTrade(const UnicodeString aPair);
void __fastcall UnSubscribeTrade(const UnicodeString aPair);
void __fastcall GetCurrentFee(const UnicodeString aPair = '');
void __fastcall GetFeeStrategy();
void __fastcall GetVolume();
void __fastcall CreateAccount(const UnicodeString aAccountId, const UnicodeString aCurrency);
void __fastcall GetAccountStatus();
void __fastcall GetOrders(const UnicodeString aClientOrderId = '', const long long aOrderId = 0, const UnicodeString aPair = '', const UnicodeString aSide = '');
void __fastcall NewOrder(const TsgcWSCexPlusOrder * aOrder);
void __fastcall NewMarketOrder(const UnicodeString aCurrency1, const UnicodeString aCurrency2, TsgcWSCexPlusSide * aSide);
void __fastcall NewLimitOrder(const UnicodeString aCurrency1, const UnicodeString aCurrency2, TsgcWSCexPlusSide * aSide, UnicodeString aPrice);
void __fastcall CancelOrder(const UnicodeString aCancelRequestId, const UnicodeString aOrderId = '', const UnicodeString aClientOrderId = '');
void __fastcall CancelAllOrders();
void __fastcall GetTransactionHistory(const UnicodeString aAccountId = '', const UnicodeString aType = '', System::TDateTime aDateFrom = 0, System::TDateTime aDateTo = 0, UnicodeString aSortOrder = '', int aPageSize = 0, int aPageNumber = 0);
void __fastcall GetFundingHistory(const UnicodeString aAccountId = '', long long aTxId = 0, const UnicodeString aDirection = '', const UnicodeString aCurrency = '', System::TDateTime aDateFrom = 0, System::TDateTime aDateTo = 0, int aPageSize = 0, int aPageNumber = 0);
void __fastcall InternalTransfer(const UnicodeString aFromAccountId, const UnicodeString aToAccountId, const UnicodeString aCurrency, const UnicodeString aAmount, const UnicodeString aClientTxId = '');
void __fastcall GetDepositAddress(const UnicodeString aAccountId, const UnicodeString aCurrency, const UnicodeString aBlockChain);
void __fastcall FundsDepositFromWallet(const UnicodeString aClientTxId, const UnicodeString aAccountId, const UnicodeString aCurrency, const UnicodeString aAmount);
void __fastcall FundsWithdrawalToWallet(const UnicodeString aClientTxId, const UnicodeString aAccountId, const UnicodeString aCurrency, const UnicodeString aAmount);
void __fastcall GetWalletBalance();
void __fastcall SubscribeAccountEvents();
void __fastcall UnSubscribeAccountEvents();
void __fastcall QueueClear();
```

