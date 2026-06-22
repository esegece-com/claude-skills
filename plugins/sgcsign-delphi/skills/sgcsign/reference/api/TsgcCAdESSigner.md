# TsgcCAdESSigner

unit: sgcSign_CAdES

Add `sgcSign_CAdES` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `KeyProvider: IsgcKeyProvider` | [IsgcKeyProvider](../types/IsgcKeyProvider.md) | `__property IsgcKeyProvider KeyProvider;` |
| `TSAClient: IsgcTSAClient` | [IsgcTSAClient](../types/IsgcTSAClient.md) | `__property IsgcTSAClient TSAClient;` |
| `OCSPClient: IsgcOCSPClient` | [IsgcOCSPClient](../types/IsgcOCSPClient.md) | `__property IsgcOCSPClient OCSPClient;` |
| `Level: TsgcCAdESLevel` | [TsgcCAdESLevel](../types/TsgcCAdESLevel.md) | `__property TsgcCAdESLevel * Level;` |
| `Detached: Boolean` | `Boolean` | `__property bool Detached;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function SignData(const aData: TBytes): TBytes;
function SignDataBase64(const aData: TBytes): string;
function SignFile(const aInputFile: string): TBytes;
function SignStream(aStream: TStream): TBytes;
procedure SaveSignatureToFile(const aSignature: TBytes; const aFileName: string);
```

C++Builder

```cpp
System::DynamicArray<System::Byte> __fastcall SignData(const System::DynamicArray<System::Byte> aData);
UnicodeString __fastcall SignDataBase64(const System::DynamicArray<System::Byte> aData);
System::DynamicArray<System::Byte> __fastcall SignFile(const UnicodeString aInputFile);
System::DynamicArray<System::Byte> __fastcall SignStream(TStream * aStream);
void __fastcall SaveSignatureToFile(const System::DynamicArray<System::Byte> aSignature, const UnicodeString aFileName);
```

