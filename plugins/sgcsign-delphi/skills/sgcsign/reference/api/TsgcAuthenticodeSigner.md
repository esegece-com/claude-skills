# TsgcAuthenticodeSigner

unit: sgcSign_Authenticode

Add `sgcSign_Authenticode` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `KeyProvider: IsgcKeyProvider` | [IsgcKeyProvider](../types/IsgcKeyProvider.md) | `__property IsgcKeyProvider KeyProvider;` |
| `TSAClient: IsgcTSAClient` | [IsgcTSAClient](../types/IsgcTSAClient.md) | `__property IsgcTSAClient TSAClient;` |
| `Hash: TsgcAuthenticodeHashAlgorithm` | [TsgcAuthenticodeHashAlgorithm](../types/TsgcAuthenticodeHashAlgorithm.md) | `__property TsgcAuthenticodeHashAlgorithm * Hash;` |
| `Level: TsgcAuthenticodeLevel` | [TsgcAuthenticodeLevel](../types/TsgcAuthenticodeLevel.md) | `__property TsgcAuthenticodeLevel * Level;` |
| `Description: string` | `string` | `__property UnicodeString Description;` |
| `URL: string` | `string` | `__property UnicodeString URL;` |
| `AppendSignature: Boolean` | `Boolean` | `__property bool AppendSignature;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function SignFile(const aInputPath, aOutputPath: string): Boolean;
function SignStream(aInput, aOutput: TStream): Boolean;
function SignBytes(const aData: TBytes): TBytes;
function SignHash(const aHash: TBytes; aHashAlg: TsgcAuthenticodeHashAlgorithm): TBytes;
```

C++Builder

```cpp
bool __fastcall SignFile(const UnicodeString aInputPath, const UnicodeString aOutputPath);
bool __fastcall SignStream(TStream * aInput, TStream * aOutput);
System::DynamicArray<System::Byte> __fastcall SignBytes(const System::DynamicArray<System::Byte> aData);
System::DynamicArray<System::Byte> __fastcall SignHash(const System::DynamicArray<System::Byte> aHash, TsgcAuthenticodeHashAlgorithm * aHashAlg);
```

