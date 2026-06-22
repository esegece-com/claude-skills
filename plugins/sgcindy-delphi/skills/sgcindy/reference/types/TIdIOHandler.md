# TIdIOHandler

kind: class
unit: IdIOHandler

## Properties

| Delphi | Type |
| --- | --- |
| `ConnectTimeout: Integer` | `Integer` |
| `ClosedGracefully: Boolean (read-only)` | `Boolean` |
| `InputBuffer: TIdBuffer (read-only)` | [TIdBuffer](./TIdBuffer.md) |
| `LargeStream: Boolean` | `Boolean` |
| `MaxCapturedLines: Integer` | `Integer` |
| `Opened: Boolean (read-only)` | `Boolean` |
| `ReadTimeout: Integer` | `Integer` |
| `ReadLnTimedout: Boolean (read-only)` | `Boolean` |
| `WriteBufferThreshold: Integer (read-only)` | `Integer` |
| `DefStringEncoding: IIdTextEncoding` | [IIdTextEncoding](./IIdTextEncoding.md) |
| `DefAnsiEncoding: IIdTextEncoding` | [IIdTextEncoding](./IIdTextEncoding.md) |
| `Destination: string` | `string` |
| `Host: string` | `string` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](./TIdConnectionIntercept.md) |
| `MaxLineLength: Integer` | `Integer` |
| `MaxLineAction: TIdMaxLineAction` | [TIdMaxLineAction](./TIdMaxLineAction.md) |
| `Port: Integer` | `Integer` |
| `RecvBufferSize: Integer` | `Integer` |
| `SendBufferSize: Integer` | `Integer` |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnWork: TWorkEvent` | [TWorkEvent](./TWorkEvent.md) |
| `OnWorkBegin: TWorkBeginEvent` | [TWorkBeginEvent](./TWorkBeginEvent.md) |
| `OnWorkEnd: TWorkEndEvent` | [TWorkEndEvent](./TWorkEndEvent.md) |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
procedure AfterAccept;
function Connected: Boolean;
procedure CheckForDisconnect(ARaiseExceptionIfDisconnected: Boolean = True; AIgnoreBuffer: Boolean = False);
function CheckForDataOnSource(ATimeout: Integer = 0): Boolean;
procedure Close;
procedure CloseGracefully;
class function MakeDefaultIOHandler(AOwner: TComponent = nil) : TIdIOHandler;
class function MakeIOHandler(ABaseType: TIdIOHandlerClass; AOwner: TComponent = nil): TIdIOHandler;
class function TryMakeIOHandler(ABaseType: TIdIOHandlerClass; AOwner: TComponent = nil): TIdIOHandler;
class procedure RegisterIOHandler;
class procedure SetDefaultClass;
function WaitFor(const AString: string; ARemoveFromBuffer: Boolean = True; AInclusive: Boolean = False; AByteEncoding: IIdTextEncoding = nil; ATimeout: Integer = IdTimeoutDefault ; AAnsiEncoding: IIdTextEncoding = nil ): string;
procedure Write(const ABuffer: TIdBytes; const ALength: Integer = -1; const AOffset: Integer = 0);
procedure WriteDirect(const ABuffer: TIdBytes; const ALength: Integer = -1; const AOffset: Integer = 0);
procedure Open;
function Readable(AMSec: Integer = IdTimeoutDefault): Boolean;
procedure WriteLn(AEncoding: IIdTextEncoding = nil);
procedure WriteLnRFC(const AOut: string = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure WriteRFCStrings(AStrings: TStrings; AWriteTerminator: Boolean = True; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
function WriteFile(const AFile: String; AEnableTransferFile: Boolean = False): Int64;
function AllData(AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function InputLn(const AMask: string = ''; AEcho: Boolean = True; ATabWidth: Integer = 8; AMaxLineLength: Integer = -1; AByteEncoding: IIdTextEncoding = nil ; AAnsiEncoding: IIdTextEncoding = nil ): string;
procedure Capture(ADest: TStream; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil );
procedure ReadBytes(var VBuffer: TIdBytes; AByteCount: Integer; AAppend: Boolean = True);
function ReadLn(AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadLnRFC(var VMsgEnd: Boolean; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadLnWait(AFailCount: Integer = MaxInt; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadLnSplit(var AWasSplit: Boolean; ATerminator: string = LF; ATimeout: Integer = IdTimeoutDefault; AMaxLineLength: Integer = -1; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadChar(AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): Char;
function ReadByte: Byte;
function ReadString(ABytes: Integer; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
function ReadInt16(AConvert: Boolean = True): Int16;
function ReadUInt16(AConvert: Boolean = True): UInt16;
function ReadInt32(AConvert: Boolean = True): Int32;
function ReadUInt32(AConvert: Boolean = True): UInt32;
function ReadInt64(AConvert: Boolean = True): Int64;
function ReadUInt64(AConvert: Boolean = True): TIdUInt64;
function ReadSmallInt(AConvert: Boolean = True): Int16;
function ReadWord(AConvert: Boolean = True): UInt16;
function ReadLongInt(AConvert: Boolean = True): Int32;
function ReadLongWord(AConvert: Boolean = True): UInt32;
procedure ReadStream(AStream: TStream; AByteCount: TIdStreamSize = -1; AReadUntilDisconnect: Boolean = False);
procedure ReadStrings(ADest: TStrings; AReadLinesCount: Integer = -1; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil );
procedure Discard(AByteCount: Int64);
procedure DiscardAll;
procedure WriteBufferCancel;
procedure WriteBufferClear;
procedure WriteBufferClose;
procedure WriteBufferFlush;
procedure WriteBufferOpen;
function WriteBufferingActive: Boolean;
function InputBufferIsEmpty: Boolean;
procedure InputBufferToStream(AStream: TStream; AByteCount: Integer = -1);
function InputBufferAsString(AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

