# TIdMessage

unit: IdMessage

Add `IdMessage` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Flags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` | `__property TIdMessageFlagsSet * Flags;` |
| `IsEncoded: Boolean` | `Boolean` | `__property bool IsEncoded;` |
| `MsgId: string` | `string` | `__property UnicodeString MsgId;` |
| `Headers: TIdHeaderList` | [TIdHeaderList](../types/TIdHeaderList.md) | `__property TIdHeaderList * Headers;` |
| `MessageParts: TIdMessageParts (read-only)` | [TIdMessageParts](../types/TIdMessageParts.md) | `__property TIdMessageParts * MessageParts /* read-only */;` |
| `MIMEBoundary: TIdMIMEBoundary (read-only)` | [TIdMIMEBoundary](../types/TIdMIMEBoundary.md) | `__property TIdMIMEBoundary * MIMEBoundary /* read-only */;` |
| `UID: String` | `String` | `__property UnicodeString UID;` |
| `IsMsgSinglePartMime: Boolean` | `Boolean` | `__property bool IsMsgSinglePartMime;` |
| `AttachmentEncoding: string` | `string` | `__property UnicodeString AttachmentEncoding;` |
| `Body: TStrings` | `TStrings` | `__property TStrings * Body;` |
| `BccList: TIdEmailAddressList` | [TIdEmailAddressList](../types/TIdEmailAddressList.md) | `__property TIdEmailAddressList * BccList;` |
| `CharSet: string` | `string` | `__property UnicodeString CharSet;` |
| `CCList: TIdEmailAddressList` | [TIdEmailAddressList](../types/TIdEmailAddressList.md) | `__property TIdEmailAddressList * CCList;` |
| `ContentType: string` | `string` | `__property UnicodeString ContentType;` |
| `ContentTransferEncoding: string` | `string` | `__property UnicodeString ContentTransferEncoding;` |
| `ContentDisposition: string` | `string` | `__property UnicodeString ContentDisposition;` |
| `Date: TDateTime` | `TDateTime` | `__property System::TDateTime Date;` |
| `Encoding: TIdMessageEncoding` | [TIdMessageEncoding](../types/TIdMessageEncoding.md) | `__property TIdMessageEncoding * Encoding;` |
| `ExtraHeaders: TIdHeaderList` | [TIdHeaderList](../types/TIdHeaderList.md) | `__property TIdHeaderList * ExtraHeaders;` |
| `FromList: TIdEmailAddressList` | [TIdEmailAddressList](../types/TIdEmailAddressList.md) | `__property TIdEmailAddressList * FromList;` |
| `From: TIdEmailAddressItem` | [TIdEmailAddressItem](../types/TIdEmailAddressItem.md) | `__property TIdEmailAddressItem * From;` |
| `NewsGroups: TStrings` | `TStrings` | `__property TStrings * NewsGroups;` |
| `NoEncode: Boolean` | `Boolean` | `__property bool NoEncode;` |
| `NoDecode: Boolean` | `Boolean` | `__property bool NoDecode;` |
| `Organization: string` | `string` | `__property UnicodeString Organization;` |
| `Priority: TIdMessagePriority` | [TIdMessagePriority](../types/TIdMessagePriority.md) | `__property TIdMessagePriority * Priority;` |
| `ReceiptRecipient: TIdEmailAddressItem` | [TIdEmailAddressItem](../types/TIdEmailAddressItem.md) | `__property TIdEmailAddressItem * ReceiptRecipient;` |
| `Recipients: TIdEmailAddressList` | [TIdEmailAddressList](../types/TIdEmailAddressList.md) | `__property TIdEmailAddressList * Recipients;` |
| `References: string` | `string` | `__property UnicodeString References;` |
| `InReplyTo: String` | `String` | `__property UnicodeString InReplyTo;` |
| `ReplyTo: TIdEmailAddressList` | [TIdEmailAddressList](../types/TIdEmailAddressList.md) | `__property TIdEmailAddressList * ReplyTo;` |
| `Subject: string` | `string` | `__property UnicodeString Subject;` |
| `Sender: TIdEmailAddressItem` | [TIdEmailAddressItem](../types/TIdEmailAddressItem.md) | `__property TIdEmailAddressItem * Sender;` |
| `UseNowForDate: Boolean` | `Boolean` | `__property bool UseNowForDate;` |
| `LastGeneratedHeaders: TIdHeaderList (read-only)` | [TIdHeaderList](../types/TIdHeaderList.md) | `__property TIdHeaderList * LastGeneratedHeaders /* read-only */;` |
| `ConvertPreamble: Boolean` | `Boolean` | `__property bool ConvertPreamble;` |
| `ExceptionOnBlockedAttachments: Boolean` | `Boolean` | `__property bool ExceptionOnBlockedAttachments;` |
| `AttachmentTempDirectory: string` | `string` | `__property UnicodeString AttachmentTempDirectory;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnInitializeISO: TIdInitializeIsoEvent` | [TIdInitializeIsoEvent](../types/TIdInitializeIsoEvent.md) | `__property TIdInitializeIsoEvent OnInitializeISO;` |
| `OnCreateAttachment: TIdCreateAttachmentEvent` | [TIdCreateAttachmentEvent](../types/TIdCreateAttachmentEvent.md) | `__property TIdCreateAttachmentEvent OnCreateAttachment;` |

## Methods

Delphi

```pascal
procedure AddHeader(const AValue: string);
procedure Clear;
procedure ClearBody;
procedure ClearHeader;
procedure GenerateHeader;
procedure InitializeISO(var VHeaderEncoding: Char; var VCharSet: String);
function IsBodyEncodingRequired: Boolean;
function IsBodyEmpty: Boolean;
procedure LoadFromFile(const AFileName: string; const AHeadersOnly: Boolean = False);
procedure LoadFromStream(AStream: TStream; const AHeadersOnly: Boolean = False);
procedure ProcessHeaders;
procedure SaveToFile(const AFileName : string; const AHeadersOnly: Boolean = False);
procedure SaveToStream(AStream: TStream; const AHeadersOnly: Boolean = False);
procedure DoCreateAttachment(const AHeaders: TStrings; var VAttachment: TIdAttachment);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall AddHeader(const UnicodeString AValue);
void __fastcall Clear();
void __fastcall ClearBody();
void __fastcall ClearHeader();
void __fastcall GenerateHeader();
void __fastcall InitializeISO(wchar_t &VHeaderEncoding, UnicodeString &VCharSet);
bool __fastcall IsBodyEncodingRequired();
bool __fastcall IsBodyEmpty();
void __fastcall LoadFromFile(const UnicodeString AFileName, const bool AHeadersOnly = False);
void __fastcall LoadFromStream(TStream * AStream, const bool AHeadersOnly = False);
void __fastcall ProcessHeaders();
void __fastcall SaveToFile(const UnicodeString AFileName, const bool AHeadersOnly = False);
void __fastcall SaveToStream(TStream * AStream, const bool AHeadersOnly = False);
void __fastcall DoCreateAttachment(const TStrings * AHeaders, TIdAttachment * &VAttachment);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

