# TsgcWhatsApp_Client

unit: sgcLibs
Edition: requires SGC_WHATSAPP

Add `sgcLibs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Log: Boolean` | `Boolean` | `__property bool Log;` |
| `LogOptions: TsgcWhatsAppLogFile` | [TsgcWhatsAppLogFile](../types/TsgcWhatsAppLogFile.md) | `__property TsgcWhatsAppLogFile * LogOptions;` |
| `TLSOptions: TsgcWhatsAppTLS_Options` | [TsgcWhatsAppTLS_Options](../types/TsgcWhatsAppTLS_Options.md) | `__property TsgcWhatsAppTLS_Options * TLSOptions;` |
| `WhatsAppOptions: TsgcWhatsApp_Client_Options` | [TsgcWhatsApp_Client_Options](../types/TsgcWhatsApp_Client_Options.md) | `__property TsgcWhatsApp_Client_Options * WhatsAppOptions;` |
| `ServerOptions: TsgcWhatsApp_Server_Options` | [TsgcWhatsApp_Server_Options](../types/TsgcWhatsApp_Server_Options.md) | `__property TsgcWhatsApp_Server_Options * ServerOptions;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeSubscribe: TsgcOnWhatsAppServerBeforeSubscribe` | [TsgcOnWhatsAppServerBeforeSubscribe](../types/TsgcOnWhatsAppServerBeforeSubscribe.md) | `__property TsgcOnWhatsAppServerBeforeSubscribe * OnBeforeSubscribe;` |
| `OnBeforeSendMessage: TsgcOnWhatsAppClientBeforeSendMessage` | [TsgcOnWhatsAppClientBeforeSendMessage](../types/TsgcOnWhatsAppClientBeforeSendMessage.md) | `__property TsgcOnWhatsAppClientBeforeSendMessage * OnBeforeSendMessage;` |
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnMessageReceived: TsgcOnWhatsAppClientMessageReceived` | [TsgcOnWhatsAppClientMessageReceived](../types/TsgcOnWhatsAppClientMessageReceived.md) | `__property TsgcOnWhatsAppClientMessageReceived * OnMessageReceived;` |
| `OnMessageSent: TsgcOnWhatsAppClientMessageSent` | [TsgcOnWhatsAppClientMessageSent](../types/TsgcOnWhatsAppClientMessageSent.md) | `__property TsgcOnWhatsAppClientMessageSent * OnMessageSent;` |

## Methods

Delphi

```pascal
procedure StartServer;
procedure StopServer;
function UploadMedia(const aFileName, aFileType: string; aPhoneNumberId: String = ''): string;
function SendTest(const aTo: string; aPhoneNumberId: string = ''): string;
function SendMessageText(const aTo, aMessage: string; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageImage(const aTo, aLink: string; const aCaption: string = ''; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageDocument(const aTo, aLink: string; const aCaption: string = ''; const aFileName: string = ''; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageAudio(const aTo, aLink: string; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageVideo(const aTo, aLink: string; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageSticker(const aTo, aLink: string; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageReaction(const aTo, aMessageId, aEmoji: string; aPhoneNumberId: string = ''): string;
function DeleteMedia(const aObjectId: string): string;
procedure DownloadMedia(const aObjectId: string; var aStream: TStream);
function SendFileImage(const aTo, aFileName, aFileType: string; const aCaption: string = ''; aPhoneNumberId: string = ''): string;
function SendFileDocument(const aTo, aFileName, aFileType: string; const aCaption: string = ''; aPhoneNumberId: string = ''): string;
function SendFileAudio(const aTo, aFileName, aFileType: string; aPhoneNumberId: string = ''): string;
function SendFileVideo(const aTo, aFileName, aFileType: string; aPhoneNumberId: string = ''): string;
function SendFileSticker(const aTo, aFileName, aFileType: string; aPhoneNumberId: string = ''): string;
function SendMessageLocation(const aTo, aLongitude, aLatitude: string; const aName: string = ''; const aAddress: string = ''; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageContact(const aTo, aName, aPhone: string; const aEmail: string = ''; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageInteractiveList(const aTo, aHeader, aBody, aFooter, aButtonText: string; aRows: Array of Const; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageInteractiveButtons(const aTo, aHeader, aBody, aFooter, aButtonText: string; aButtons: Array of Const; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function SendMessageTemplate(const aTo, aTemplate, aLanguageCode: string; aPhoneNumberId: string = ''; const aOptions: TsgcWhatsApp_Message_Options = nil): string;
function MarkMessageRead(const aMessageId: string; aPhoneNumberId: string = ''): Boolean;
```

C++Builder

```cpp
void __fastcall StartServer();
void __fastcall StopServer();
UnicodeString __fastcall UploadMedia(const UnicodeString aFileName, const UnicodeString aFileType, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendTest(const UnicodeString aTo, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendMessageText(const UnicodeString aTo, const UnicodeString aMessage, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageImage(const UnicodeString aTo, const UnicodeString aLink, const UnicodeString aCaption = '', UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageDocument(const UnicodeString aTo, const UnicodeString aLink, const UnicodeString aCaption = '', const UnicodeString aFileName = '', UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageAudio(const UnicodeString aTo, const UnicodeString aLink, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageVideo(const UnicodeString aTo, const UnicodeString aLink, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageSticker(const UnicodeString aTo, const UnicodeString aLink, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageReaction(const UnicodeString aTo, const UnicodeString aMessageId, const UnicodeString aEmoji, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall DeleteMedia(const UnicodeString aObjectId);
void __fastcall DownloadMedia(const UnicodeString aObjectId, TStream * &aStream);
UnicodeString __fastcall SendFileImage(const UnicodeString aTo, const UnicodeString aFileName, const UnicodeString aFileType, const UnicodeString aCaption = '', UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendFileDocument(const UnicodeString aTo, const UnicodeString aFileName, const UnicodeString aFileType, const UnicodeString aCaption = '', UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendFileAudio(const UnicodeString aTo, const UnicodeString aFileName, const UnicodeString aFileType, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendFileVideo(const UnicodeString aTo, const UnicodeString aFileName, const UnicodeString aFileType, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendFileSticker(const UnicodeString aTo, const UnicodeString aFileName, const UnicodeString aFileType, UnicodeString aPhoneNumberId = '');
UnicodeString __fastcall SendMessageLocation(const UnicodeString aTo, const UnicodeString aLongitude, const UnicodeString aLatitude, const UnicodeString aName = '', const UnicodeString aAddress = '', UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageContact(const UnicodeString aTo, const UnicodeString aName, const UnicodeString aPhone, const UnicodeString aEmail = '', UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageInteractiveList(const UnicodeString aTo, const UnicodeString aHeader, const UnicodeString aBody, const UnicodeString aFooter, const UnicodeString aButtonText, Array of Const aRows, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageInteractiveButtons(const UnicodeString aTo, const UnicodeString aHeader, const UnicodeString aBody, const UnicodeString aFooter, const UnicodeString aButtonText, Array of Const aButtons, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
UnicodeString __fastcall SendMessageTemplate(const UnicodeString aTo, const UnicodeString aTemplate, const UnicodeString aLanguageCode, UnicodeString aPhoneNumberId = '', const TsgcWhatsApp_Message_Options * aOptions = nil);
bool __fastcall MarkMessageRead(const UnicodeString aMessageId, UnicodeString aPhoneNumberId = '');
```

