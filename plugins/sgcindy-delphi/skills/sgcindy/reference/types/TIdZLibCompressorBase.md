# TIdZLibCompressorBase

kind: class
unit: IdZLibCompressorBase

## Properties

| Delphi | Type |
| --- | --- |
| `IsReady: Boolean (read-only)` | `Boolean` |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
procedure DeflateStream(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel=0);
procedure InflateStream(AInStream, AOutStream : TStream);
procedure CompressStream(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel; const AWindowBits, AMemLevel, AStrategy: Integer);
procedure DecompressStream(AInStream, AOutStream : TStream; const AWindowBits : Integer);
procedure DecompressDeflateStream(AInStream, AOutStream : TStream);
procedure CompressFTPDeflate(AInStream, AOutStream : TStream; const ALevel, AWindowBits, AMemLevel, AStrategy: Integer);
procedure CompressFTPToIO(AInStream : TStream; AIOHandler : TIdIOHandler; const ALevel, AWindowBits, AMemLevel, AStrategy: Integer);
procedure DecompressFTPFromIO(AIOHandler : TIdIOHandler; AOutputStream : TStream; const AWindowBits : Integer);
procedure DecompressFTPDeflate(AInStream, AOutStream : TStream; const AWindowBits : Integer);
procedure CompressHTTPDeflate(AInStream, AOutStream : TStream; const ALevel : TIdCompressionLevel);
procedure DecompressHTTPDeflate(AInStream, AOutStream : TStream);
procedure DecompressGZipStream(AInStream, AOutStream : TStream);
procedure RemoveFreeNotification(AComponent: TComponent);
```

