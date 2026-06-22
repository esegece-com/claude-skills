# TsgcWSAPI_XTB

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `XTB: TsgcWSXTB_Options` | [TsgcWSXTB_Options](../types/TsgcWSXTB_Options.md) | `__property TsgcWSXTB_Options * XTB;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnXTBConnect: TsgcWSXTBConnectEvent` | [TsgcWSXTBConnectEvent](../types/TsgcWSXTBConnectEvent.md) | `__property TsgcWSXTBConnectEvent OnXTBConnect;` |
| `OnXTBMessage: TsgcWSXTBMessageEvent` | [TsgcWSXTBMessageEvent](../types/TsgcWSXTBMessageEvent.md) | `__property TsgcWSXTBMessageEvent OnXTBMessage;` |
| `OnXTBError: TsgcWSXTBErrorEvent` | [TsgcWSXTBErrorEvent](../types/TsgcWSXTBErrorEvent.md) | `__property TsgcWSXTBErrorEvent OnXTBError;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Login;
procedure Logout;
procedure GetAllSymbols;
procedure GetCalendar;
procedure GetChartLastRequest(const aSymbol: string; aPeriod: TsgcWSXTBPeriod; aStart: TDateTime);
procedure GetChartRangeRequest(const aSymbol: string; aPeriod: TsgcWSXTBPeriod; aStart, aEnd: TDateTime; aTicks: Integer = 0);
procedure GetCommissionDef(const aSymbol: string; aVolume: Double);
procedure GetCurrentUserData;
procedure GetIbsHistory(aStart, aEnd: TDateTime);
procedure GetMarginLevel;
procedure GetMarginTrade(const aSymbol: string; aVolume: Double);
procedure GetNews(aStart: TDateTime; aEnd: TDateTime = 0);
procedure GetProfitCalculation(aClosePrice: Double; aCmd: TsgcWSXTBCmd; aOpenPrice: Double; const aSymbol: string; aVolume: Double);
procedure GetServerTime;
procedure GetStepRules;
procedure GetSymbol(const aSymbol: string);
procedure GetTickPrices(const aSymbol: string; aLevel: Integer; aTimestamp: TDateTime);
procedure GetTradeRecords(aOrder: Int64);
procedure GetTrades(aOpenedOnly: Boolean = true);
procedure GetTradesHistory(aStart: TDateTime; aEnd: TDateTime = 0);
procedure GetTradingHours(const aSymbol: string);
procedure GetVersion;
procedure Ping;
procedure TradeTransaction(aCmd: TsgcWSXTBCmd; const aCustomContent: string; aExpiration: TDateTime; aOffset: Integer; aOrder: Int64; aPrice, aStopLoss: Double; const aSymbol: string; aTakeProfit: Double; aType: TsgcWSXTBType; aVolume: Double);
procedure TradeTransactionStatus(const aOrder: Int64);
procedure SubscribeBalance;
procedure UnSubscribeBalance;
procedure SubscribeCandles(const aSymbol: string);
procedure UnSubscribeCandles(const aSymbol: string);
procedure SubscribeKeepAlive;
procedure UnSubscribeKeepAlive;
procedure SubscribeNews;
procedure UnSubscribeNews;
procedure SubscribeProfits;
procedure UnSubscribeProfits;
procedure SubscribeTickPrices(const aSymbol: string; aMinArrivalTime: Integer = 0; aMaxLevel: Integer = 0);
procedure UnSubscribeTickPrices(const aSymbol: string);
procedure SubscribeTrades;
procedure UnSubscribeTrades;
procedure SubscribeTradeStatus;
procedure UnSubscribeTradeStatus;
procedure SubscribePing;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Login();
void __fastcall Logout();
void __fastcall GetAllSymbols();
void __fastcall GetCalendar();
void __fastcall GetChartLastRequest(const UnicodeString aSymbol, TsgcWSXTBPeriod * aPeriod, System::TDateTime aStart);
void __fastcall GetChartRangeRequest(const UnicodeString aSymbol, TsgcWSXTBPeriod * aPeriod, System::TDateTime aStart, System::TDateTime aEnd, int aTicks = 0);
void __fastcall GetCommissionDef(const UnicodeString aSymbol, double aVolume);
void __fastcall GetCurrentUserData();
void __fastcall GetIbsHistory(System::TDateTime aStart, System::TDateTime aEnd);
void __fastcall GetMarginLevel();
void __fastcall GetMarginTrade(const UnicodeString aSymbol, double aVolume);
void __fastcall GetNews(System::TDateTime aStart, System::TDateTime aEnd = 0);
void __fastcall GetProfitCalculation(double aClosePrice, TsgcWSXTBCmd * aCmd, double aOpenPrice, const UnicodeString aSymbol, double aVolume);
void __fastcall GetServerTime();
void __fastcall GetStepRules();
void __fastcall GetSymbol(const UnicodeString aSymbol);
void __fastcall GetTickPrices(const UnicodeString aSymbol, int aLevel, System::TDateTime aTimestamp);
void __fastcall GetTradeRecords(long long aOrder);
void __fastcall GetTrades(bool aOpenedOnly = true);
void __fastcall GetTradesHistory(System::TDateTime aStart, System::TDateTime aEnd = 0);
void __fastcall GetTradingHours(const UnicodeString aSymbol);
void __fastcall GetVersion();
void __fastcall Ping();
void __fastcall TradeTransaction(TsgcWSXTBCmd * aCmd, const UnicodeString aCustomContent, System::TDateTime aExpiration, int aOffset, long long aOrder, double aPrice, double aStopLoss, const UnicodeString aSymbol, double aTakeProfit, TsgcWSXTBType * aType, double aVolume);
void __fastcall TradeTransactionStatus(const long long aOrder);
void __fastcall SubscribeBalance();
void __fastcall UnSubscribeBalance();
void __fastcall SubscribeCandles(const UnicodeString aSymbol);
void __fastcall UnSubscribeCandles(const UnicodeString aSymbol);
void __fastcall SubscribeKeepAlive();
void __fastcall UnSubscribeKeepAlive();
void __fastcall SubscribeNews();
void __fastcall UnSubscribeNews();
void __fastcall SubscribeProfits();
void __fastcall UnSubscribeProfits();
void __fastcall SubscribeTickPrices(const UnicodeString aSymbol, int aMinArrivalTime = 0, int aMaxLevel = 0);
void __fastcall UnSubscribeTickPrices(const UnicodeString aSymbol);
void __fastcall SubscribeTrades();
void __fastcall UnSubscribeTrades();
void __fastcall SubscribeTradeStatus();
void __fastcall UnSubscribeTradeStatus();
void __fastcall SubscribePing();
void __fastcall QueueClear();
```

