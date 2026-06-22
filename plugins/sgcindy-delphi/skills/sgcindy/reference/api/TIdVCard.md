# TIdVCard

unit: IdVCard

Add `IdVCard` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `RawForm: TStrings (read-only)` | `TStrings` | `__property TStrings * RawForm /* read-only */;` |
| `VCardVersion: Real (read-only)` | `Real` | `__property double VCardVersion /* read-only */;` |
| `URLs: TStrings` | `TStrings` | `__property TStrings * URLs;` |
| `ProductID: String` | `String` | `__property UnicodeString ProductID;` |
| `UniqueID: String` | `String` | `__property UnicodeString UniqueID;` |
| `Classification: String` | `String` | `__property UnicodeString Classification;` |
| `BirthDay: TDateTime` | `TDateTime` | `__property System::TDateTime BirthDay;` |
| `FullName: TIdVCardName` | [TIdVCardName](../types/TIdVCardName.md) | `__property TIdVCardName * FullName;` |
| `EMailProgram: String` | `String` | `__property UnicodeString EMailProgram;` |
| `EMailAddresses: TIdVCardEMailAddresses (read-only)` | [TIdVCardEMailAddresses](../types/TIdVCardEMailAddresses.md) | `__property TIdVCardEMailAddresses * EMailAddresses /* read-only */;` |
| `Telephones: TIdVCardTelephones (read-only)` | [TIdVCardTelephones](../types/TIdVCardTelephones.md) | `__property TIdVCardTelephones * Telephones /* read-only */;` |
| `BusinessInfo: TIdVCardBusinessInfo (read-only)` | [TIdVCardBusinessInfo](../types/TIdVCardBusinessInfo.md) | `__property TIdVCardBusinessInfo * BusinessInfo /* read-only */;` |
| `Categories: TStrings` | `TStrings` | `__property TStrings * Categories;` |
| `Addresses: TIdVCardAddresses (read-only)` | [TIdVCardAddresses](../types/TIdVCardAddresses.md) | `__property TIdVCardAddresses * Addresses /* read-only */;` |
| `MailingLabels: TIdVCardMailingLabels (read-only)` | [TIdVCardMailingLabels](../types/TIdVCardMailingLabels.md) | `__property TIdVCardMailingLabels * MailingLabels /* read-only */;` |
| `Comments: TStrings` | `TStrings` | `__property TStrings * Comments;` |
| `Photo: TIdVCardEmbeddedObject (read-only)` | [TIdVCardEmbeddedObject](../types/TIdVCardEmbeddedObject.md) | `__property TIdVCardEmbeddedObject * Photo /* read-only */;` |
| `Logo: TIdVCardEmbeddedObject (read-only)` | [TIdVCardEmbeddedObject](../types/TIdVCardEmbeddedObject.md) | `__property TIdVCardEmbeddedObject * Logo /* read-only */;` |
| `Sound: TIdVCardEmbeddedObject (read-only)` | [TIdVCardEmbeddedObject](../types/TIdVCardEmbeddedObject.md) | `__property TIdVCardEmbeddedObject * Sound /* read-only */;` |
| `Key: TIdVCardEmbeddedObject (read-only)` | [TIdVCardEmbeddedObject](../types/TIdVCardEmbeddedObject.md) | `__property TIdVCardEmbeddedObject * Key /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure ReadFromStrings(s : TStrings);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall ReadFromStrings(TStrings * s);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

