# TIdMessage

kind: class
unit: IdMessage

## Properties

| Delphi | Type |
| --- | --- |
| `Flags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` |
| `IsEncoded: Boolean` | `Boolean` |
| `MsgId: string` | `string` |
| `Headers: TIdHeaderList` | `TIdHeaderList` |
| `MessageParts: TIdMessageParts (read-only)` | `TIdMessageParts` |
| `MIMEBoundary: TIdMIMEBoundary (read-only)` | `TIdMIMEBoundary` |
| `UID: String` | `String` |
| `IsMsgSinglePartMime: Boolean` | `Boolean` |
| `AttachmentEncoding: string` | `string` |
| `Body: TStrings` | `TStrings` |
| `BccList: TIdEmailAddressList` | `TIdEmailAddressList` |
| `CharSet: string` | `string` |
| `CCList: TIdEmailAddressList` | `TIdEmailAddressList` |
| `ContentType: string` | `string` |
| `ContentTransferEncoding: string` | `string` |
| `ContentDisposition: string` | `string` |
| `Date: TDateTime` | `TDateTime` |
| `Encoding: TIdMessageEncoding` | `TIdMessageEncoding` |
| `ExtraHeaders: TIdHeaderList` | `TIdHeaderList` |
| `FromList: TIdEmailAddressList` | `TIdEmailAddressList` |
| `From: TIdEmailAddressItem` | `TIdEmailAddressItem` |
| `NewsGroups: TStrings` | `TStrings` |
| `NoEncode: Boolean` | `Boolean` |
| `NoDecode: Boolean` | `Boolean` |
| `Organization: string` | `string` |
| `Priority: TIdMessagePriority` | `TIdMessagePriority` |
| `ReceiptRecipient: TIdEmailAddressItem` | `TIdEmailAddressItem` |
| `Recipients: TIdEmailAddressList` | `TIdEmailAddressList` |
| `References: string` | `string` |
| `InReplyTo: String` | `String` |
| `ReplyTo: TIdEmailAddressList` | `TIdEmailAddressList` |
| `Subject: string` | `string` |
| `Sender: TIdEmailAddressItem` | `TIdEmailAddressItem` |
| `UseNowForDate: Boolean` | `Boolean` |
| `LastGeneratedHeaders: TIdHeaderList (read-only)` | `TIdHeaderList` |
| `ConvertPreamble: Boolean` | `Boolean` |
| `ExceptionOnBlockedAttachments: Boolean` | `Boolean` |
| `AttachmentTempDirectory: string` | `string` |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnInitializeISO: TIdInitializeIsoEvent` | `TIdInitializeIsoEvent` |
| `OnCreateAttachment: TIdCreateAttachmentEvent` | `TIdCreateAttachmentEvent` |

## Methods

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

