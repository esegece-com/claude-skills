# TIdCompressorZLib

unit: IdCompressorZLib

Add `IdCompressorZLib` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `IsReady: Boolean (read-only)` | `Boolean` | `__property bool IsReady /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure DeflateStream(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel=0);
procedure InflateStream(AInStream, AOutStream : TStream);
procedure CompressStream(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel; const AWindowBits, AMemLevel, AStrategy: Integer);
procedure DecompressStream(AInStream, AOutStream : TStream; const AWindowBits : Integer);
procedure CompressFTPToIO(AInStream : TStream; AIOHandler : TIdIOHandler; const ALevel, AWindowBits, AMemLevel, AStrategy: Integer);
procedure DecompressFTPFromIO(AIOHandler : TIdIOHandler; AOutputStream : TStream; const AWindowBits : Integer);
procedure DecompressDeflateStream(AInStream, AOutStream : TStream);
procedure CompressFTPDeflate(AInStream, AOutStream : TStream; const ALevel, AWindowBits, AMemLevel, AStrategy: Integer);
procedure DecompressFTPDeflate(AInStream, AOutStream : TStream; const AWindowBits : Integer);
procedure CompressHTTPDeflate(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel);
procedure DecompressHTTPDeflate(AInStream, AOutStream : TStream);
procedure DecompressGZipStream(AInStream, AOutStream : TStream);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall DeflateStream(TStream * AInStream, TStream * AOutStream, const TIdCompressionLevel * ALevel = 0);
void __fastcall InflateStream(TStream * AInStream, TStream * AOutStream);
void __fastcall CompressStream(TStream * AInStream, TStream * AOutStream, const TIdCompressionLevel * ALevel, const int AWindowBits, const int AMemLevel, const int AStrategy);
void __fastcall DecompressStream(TStream * AInStream, TStream * AOutStream, const int AWindowBits);
void __fastcall CompressFTPToIO(TStream * AInStream, TIdIOHandler * AIOHandler, const int ALevel, const int AWindowBits, const int AMemLevel, const int AStrategy);
void __fastcall DecompressFTPFromIO(TIdIOHandler * AIOHandler, TStream * AOutputStream, const int AWindowBits);
void __fastcall DecompressDeflateStream(TStream * AInStream, TStream * AOutStream);
void __fastcall CompressFTPDeflate(TStream * AInStream, TStream * AOutStream, const int ALevel, const int AWindowBits, const int AMemLevel, const int AStrategy);
void __fastcall DecompressFTPDeflate(TStream * AInStream, TStream * AOutStream, const int AWindowBits);
void __fastcall CompressHTTPDeflate(TStream * AInStream, TStream * AOutStream, const TIdCompressionLevel * ALevel);
void __fastcall DecompressHTTPDeflate(TStream * AInStream, TStream * AOutStream);
void __fastcall DecompressGZipStream(TStream * AInStream, TStream * AOutStream);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

