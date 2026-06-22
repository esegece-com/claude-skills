# TsgcWSAPI_HTX

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Huobi: TsgcWSHuobi_Options` | [TsgcWSHuobi_Options](../types/TsgcWSHuobi_Options.md) | `__property TsgcWSHuobi_Options * Huobi;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnHuobiSubscribed: TsgcWSHuobiSubscribedEvent` | [TsgcWSHuobiSubscribedEvent](../types/TsgcWSHuobiSubscribedEvent.md) | `__property TsgcWSHuobiSubscribedEvent OnHuobiSubscribed;` |
| `OnHuobiUnSubscribed: TsgcWSHuobiUnSubscribedEvent` | [TsgcWSHuobiUnSubscribedEvent](../types/TsgcWSHuobiUnSubscribedEvent.md) | `__property TsgcWSHuobiUnSubscribedEvent OnHuobiUnSubscribed;` |
| `OnHuobiUpdate: TsgcWSHuobiUpdateEvent` | [TsgcWSHuobiUpdateEvent](../types/TsgcWSHuobiUpdateEvent.md) | `__property TsgcWSHuobiUpdateEvent OnHuobiUpdate;` |
| `OnHuobiError: TsgcWSHuobiErrorEvent` | [TsgcWSHuobiErrorEvent](../types/TsgcWSHuobiErrorEvent.md) | `__property TsgcWSHuobiErrorEvent OnHuobiError;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
procedure Ping;
procedure SubscribeKLine(const aSymbol: String; aPeriod: TsgcWSHuobiPeriods; const aId: String = '');
procedure UnSubscribeKLine(const aSymbol: String; aPeriod: TsgcWSHuobiPeriods; const aId: String = '');
procedure SubscribeMarketDepth(const aSymbol: String; aDepth: TsgcWSHuobiDepths; const aId: String = '');
procedure UnSubscribeMarketDepth(const aSymbol: String; aDepth: TsgcWSHuobiDepths; const aId: String = '');
procedure SubscribeTradeDetail(const aSymbol: String; const aId: String = '');
procedure UnSubscribeTradeDetail(const aSymbol: String; const aId: String = '');
procedure SubscribeMarketDetail(const aSymbol: String; const aId: String = '');
procedure UnSubscribeMarketDetail(const aSymbol: String; const aId: String = '');
procedure SubscribeBBO(const aSymbol: String; const aId: String = '');
procedure UnSubscribeBBO(const aSymbol: String; const aId: String = '');
procedure SubscribeMarketTicker(const aSymbol: String; const aId: String = '');
procedure UnSubscribeMarketTicker(const aSymbol: String; const aId: String = '');
procedure SubscribeMarketByPrice(const aSymbol: String; aLevel: TsgcWSHuobiLevels; const aId: String = '');
procedure UnSubscribeMarketByPrice(const aSymbol: String; aLevel: TsgcWSHuobiLevels; const aId: String = '');
procedure SubscribeOrderUpdates(const aSymbol: String);
procedure SubscribeTradeClearing(const aSymbol: String; aMode: Integer = 0);
procedure SubscribeAccountChange(aMode: Integer = 0);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall SubscribeKLine(const UnicodeString aSymbol, TsgcWSHuobiPeriods * aPeriod, const UnicodeString aId = '');
void __fastcall UnSubscribeKLine(const UnicodeString aSymbol, TsgcWSHuobiPeriods * aPeriod, const UnicodeString aId = '');
void __fastcall SubscribeMarketDepth(const UnicodeString aSymbol, TsgcWSHuobiDepths * aDepth, const UnicodeString aId = '');
void __fastcall UnSubscribeMarketDepth(const UnicodeString aSymbol, TsgcWSHuobiDepths * aDepth, const UnicodeString aId = '');
void __fastcall SubscribeTradeDetail(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall UnSubscribeTradeDetail(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall SubscribeMarketDetail(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall UnSubscribeMarketDetail(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall SubscribeBBO(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall UnSubscribeBBO(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall SubscribeMarketTicker(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall UnSubscribeMarketTicker(const UnicodeString aSymbol, const UnicodeString aId = '');
void __fastcall SubscribeMarketByPrice(const UnicodeString aSymbol, TsgcWSHuobiLevels * aLevel, const UnicodeString aId = '');
void __fastcall UnSubscribeMarketByPrice(const UnicodeString aSymbol, TsgcWSHuobiLevels * aLevel, const UnicodeString aId = '');
void __fastcall SubscribeOrderUpdates(const UnicodeString aSymbol);
void __fastcall SubscribeTradeClearing(const UnicodeString aSymbol, int aMode = 0);
void __fastcall SubscribeAccountChange(int aMode = 0);
void __fastcall QueueClear();
```

