# TsgcHTTP_Cryptohopper

unit: sgcLibs
Edition: Professional and higher

Add `sgcLibs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CryptohopperOptions: TsgcHTTPCryptohopper_Options` | [TsgcHTTPCryptohopper_Options](../types/TsgcHTTPCryptohopper_Options.md) | `__property TsgcHTTPCryptohopper_Options * CryptohopperOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `TLSOptions: TsgcHTTPTLS_Options` | [TsgcHTTPTLS_Options](../types/TsgcHTTPTLS_Options.md) | `__property TsgcHTTPTLS_Options * TLSOptions;` |
| `CircuitBreaker: TsgcWSCircuitBreaker` | [TsgcWSCircuitBreaker](../types/TsgcWSCircuitBreaker.md) | `__property TsgcWSCircuitBreaker * CircuitBreaker;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnWebhook: TsgcCryptohopperWebhookEvent` | [TsgcCryptohopperWebhookEvent](../types/TsgcCryptohopperWebhookEvent.md) | `__property TsgcCryptohopperWebhookEvent OnWebhook;` |
| `OnHTTPAPIException: TsgcHTTPAPIExceptionEvent` | [TsgcHTTPAPIExceptionEvent](../types/TsgcHTTPAPIExceptionEvent.md) | `__property TsgcHTTPAPIExceptionEvent OnHTTPAPIException;` |
| `OnHTTPAPISSE: TsgcHTTPAPISSEEvent` | [TsgcHTTPAPISSEEvent](../types/TsgcHTTPAPISSEEvent.md) | `__property TsgcHTTPAPISSEEvent OnHTTPAPISSE;` |

## Methods

Delphi

```pascal
procedure StartWebhook;
procedure StopWebhook;
function GetHoppers: string;
function CreateHopper(const aBody: string): string;
function GetHopper(const aId: string): string;
function DeleteHopper(const aId: string): string;
function UpdateHopper(const aId: string; const aBody: string) : string;
function GetOpenOrders(const aId: string): string;
function CreateNewOrder(const aId: string; const aOrder: TsgcHTTPCTHOrder): string;
function PlaceMarketOrder(const aId: string; aOrderSide: TsgcHTTPCTHOrderSide; const aCoin: string; aAmount: Extended): string;
function PlaceLimitOrder(const aId: string; aOrderSide: TsgcHTTPCTHOrderSide; const aCoin: string; aAmount: Extended; aPrice: Extended): string;
function DeleteOrder(const aId: string; const aOrderId: string): string;
function DeleteAllOrders(const aId: string): string;
function GetOpenOrder(const aId: string; const aOrderId: string): string;
function CancelOrder(const aId: string; const aOrderId: string): string;
function GetPosition(const aId: string): string;
function GetTradeHistory(const aId: string): string;
function GetTradeHistoryById(const aId: string; const aTradeId: string): string;
function GetExchange: string;
function GetAllTickers(const aExchange: string): string;
function GetMarketTicker(const aExchange: string; const aPair: string): string;
function GetOrderBook(const aExchange: string; const aPair: string; const aDepth: string): string;
function CreateWebhook(const aURL: string; aMessageTypes: string = ''): string;
function DeleteWebhook(const aURL: string): string;
function SendSignal(const aSignal: TsgcHTTPCTHSignal): string;
function SendTestSignal(const aSignal: TsgcHTTPCTHSignal): string;
function GetSignalStats(const aSignalId: String; const aExchange: String = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

C++Builder

```cpp
void __fastcall StartWebhook();
void __fastcall StopWebhook();
UnicodeString __fastcall GetHoppers();
UnicodeString __fastcall CreateHopper(const UnicodeString aBody);
UnicodeString __fastcall GetHopper(const UnicodeString aId);
UnicodeString __fastcall DeleteHopper(const UnicodeString aId);
UnicodeString __fastcall UpdateHopper(const UnicodeString aId, const UnicodeString aBody);
UnicodeString __fastcall GetOpenOrders(const UnicodeString aId);
UnicodeString __fastcall CreateNewOrder(const UnicodeString aId, const TsgcHTTPCTHOrder * aOrder);
UnicodeString __fastcall PlaceMarketOrder(const UnicodeString aId, TsgcHTTPCTHOrderSide * aOrderSide, const UnicodeString aCoin, long double aAmount);
UnicodeString __fastcall PlaceLimitOrder(const UnicodeString aId, TsgcHTTPCTHOrderSide * aOrderSide, const UnicodeString aCoin, long double aAmount, long double aPrice);
UnicodeString __fastcall DeleteOrder(const UnicodeString aId, const UnicodeString aOrderId);
UnicodeString __fastcall DeleteAllOrders(const UnicodeString aId);
UnicodeString __fastcall GetOpenOrder(const UnicodeString aId, const UnicodeString aOrderId);
UnicodeString __fastcall CancelOrder(const UnicodeString aId, const UnicodeString aOrderId);
UnicodeString __fastcall GetPosition(const UnicodeString aId);
UnicodeString __fastcall GetTradeHistory(const UnicodeString aId);
UnicodeString __fastcall GetTradeHistoryById(const UnicodeString aId, const UnicodeString aTradeId);
UnicodeString __fastcall GetExchange();
UnicodeString __fastcall GetAllTickers(const UnicodeString aExchange);
UnicodeString __fastcall GetMarketTicker(const UnicodeString aExchange, const UnicodeString aPair);
UnicodeString __fastcall GetOrderBook(const UnicodeString aExchange, const UnicodeString aPair, const UnicodeString aDepth);
UnicodeString __fastcall CreateWebhook(const UnicodeString aURL, UnicodeString aMessageTypes = '');
UnicodeString __fastcall DeleteWebhook(const UnicodeString aURL);
UnicodeString __fastcall SendSignal(const TsgcHTTPCTHSignal * aSignal);
UnicodeString __fastcall SendTestSignal(const TsgcHTTPCTHSignal * aSignal);
UnicodeString __fastcall GetSignalStats(const UnicodeString aSignalId, const UnicodeString aExchange = '');
UnicodeString __fastcall Get(const UnicodeString aURL, const TStrings * aHeaders = nil, bool aSSE = False);
UnicodeString __fastcall Post(const UnicodeString aURL, const UnicodeString aBody, const TStrings * aHeaders = nil, const TIdMultiPartFormDataStream * aMultipartFormData = nil, bool aForceHTTP1 = False, bool aSSE = False, const TStrings * aResponseHeaders = nil);
UnicodeString __fastcall Delete(const UnicodeString aURL, const TStrings * aHeader = nil, const UnicodeString aBody = '');
UnicodeString __fastcall Patch(const UnicodeString aURL, const UnicodeString aBody, const TStrings * aHeaders = nil);
UnicodeString __fastcall Put(const UnicodeString aURL, const UnicodeString aBody, const TStrings * aHeaders = nil);
```

