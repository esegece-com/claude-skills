# TIdMessageDecoderYenc

unit: IdMessageCoderYenc

Add `IdMessageCoderYenc` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Filename: string (read-only)` | `string` | `__property UnicodeString Filename /* read-only */;` |
| `FreeSourceStream: Boolean` | `Boolean` | `__property bool FreeSourceStream;` |
| `Headers: TStrings (read-only)` | `TStrings` | `__property TStrings * Headers /* read-only */;` |
| `PartType: TIdMessageCoderPartType (read-only)` | [TIdMessageCoderPartType](../types/TIdMessageCoderPartType.md) | `__property TIdMessageCoderPartType * PartType /* read-only */;` |
| `SourceStream: TStream` | `TStream` | `__property TStream * SourceStream;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
function ReadBody(ADestStream: TStream; var AMsgEnd: Boolean): TIdMessageDecoder;
procedure ReadHeader;
function ReadLn(const ATerminator: string = LF; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadLnRFC(var VMsgEnd: Boolean; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): String;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdMessageDecoder * __fastcall ReadBody(TStream * ADestStream, bool &AMsgEnd);
void __fastcall ReadHeader();
UnicodeString __fastcall ReadLn(const UnicodeString ATerminator = LF, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall ReadLnRFC(bool &VMsgEnd, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

