# TIdSSLIOHandlerSocketOpenSSL

unit: IdSSLOpenSSL

Add `IdSSLOpenSSL` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `SSLSocket: TIdSSLSocket` | [TIdSSLSocket](../types/TIdSSLSocket.md) | `__property TIdSSLSocket * SSLSocket;` |
| `SSLContext: TIdSSLContext` | [TIdSSLContext](../types/TIdSSLContext.md) | `__property TIdSSLContext * SSLContext;` |
| `ALPNProtocols: TStringList` | `TStringList` | `__property TStringList * ALPNProtocols;` |
| `SSL_HandShake: Boolean (read-only)` | `Boolean` | `__property bool SSL_HandShake /* read-only */;` |
| `SSLOptions: TIdSSLOptions` | [TIdSSLOptions](../types/TIdSSLOptions.md) | `__property TIdSSLOptions * SSLOptions;` |
| `PassThrough: Boolean` | `Boolean` | `__property bool PassThrough;` |
| `IsPeer: Boolean` | `Boolean` | `__property bool IsPeer;` |
| `URIToCheck: String` | `String` | `__property UnicodeString URIToCheck;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](../types/TIdSocketHandle.md) | `__property TIdSocketHandle * Binding /* read-only */;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `TransparentProxy: TIdCustomTransparentProxy` | [TIdCustomTransparentProxy](../types/TIdCustomTransparentProxy.md) | `__property TIdCustomTransparentProxy * TransparentProxy;` |
| `UseNagle: boolean` | `boolean` | `__property bool UseNagle;` |
| `LingerState: Integer` | `Integer` | `__property int LingerState;` |
| `IO: Boolean` | `Boolean` | `__property bool IO;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `ClosedGracefully: Boolean (read-only)` | `Boolean` | `__property bool ClosedGracefully /* read-only */;` |
| `InputBuffer: TIdBuffer (read-only)` | [TIdBuffer](../types/TIdBuffer.md) | `__property TIdBuffer * InputBuffer /* read-only */;` |
| `LargeStream: Boolean` | `Boolean` | `__property bool LargeStream;` |
| `MaxCapturedLines: Integer` | `Integer` | `__property int MaxCapturedLines;` |
| `Opened: Boolean (read-only)` | `Boolean` | `__property bool Opened /* read-only */;` |
| `ReadLnTimedout: Boolean (read-only)` | `Boolean` | `__property bool ReadLnTimedout /* read-only */;` |
| `WriteBufferThreshold: Integer (read-only)` | `Integer` | `__property int WriteBufferThreshold /* read-only */;` |
| `DefStringEncoding: IIdTextEncoding` | [IIdTextEncoding](../types/IIdTextEncoding.md) | `__property IIdTextEncoding DefStringEncoding;` |
| `DefAnsiEncoding: IIdTextEncoding` | [IIdTextEncoding](../types/IIdTextEncoding.md) | `__property IIdTextEncoding DefAnsiEncoding;` |
| `Destination: string` | `string` | `__property UnicodeString Destination;` |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](../types/TIdConnectionIntercept.md) | `__property TIdConnectionIntercept * Intercept;` |
| `MaxLineLength: Integer` | `Integer` | `__property int MaxLineLength;` |
| `MaxLineAction: TIdMaxLineAction` | [TIdMaxLineAction](../types/TIdMaxLineAction.md) | `__property TIdMaxLineAction * MaxLineAction;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `RecvBufferSize: Integer` | `Integer` | `__property int RecvBufferSize;` |
| `SendBufferSize: Integer` | `Integer` | `__property int SendBufferSize;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeConnect: TIOHandlerNotify` | [TIOHandlerNotify](../types/TIOHandlerNotify.md) | `__property TIOHandlerNotify OnBeforeConnect;` |
| `OnStatusInfo: TCallbackEvent` | [TCallbackEvent](../types/TCallbackEvent.md) | `__property TCallbackEvent OnStatusInfo;` |
| `OnStatusInfoEx: TCallbackExEvent` | [TCallbackExEvent](../types/TCallbackExEvent.md) | `__property TCallbackExEvent OnStatusInfoEx;` |
| `OnGetPassword: TPasswordEvent` | [TPasswordEvent](../types/TPasswordEvent.md) | `__property TPasswordEvent OnGetPassword;` |
| `OnGetPasswordEx: TPasswordEventEx` | [TPasswordEventEx](../types/TPasswordEventEx.md) | `__property TPasswordEventEx * OnGetPasswordEx;` |
| `OnVerifyPeer: TVerifyPeerEvent` | [TVerifyPeerEvent](../types/TVerifyPeerEvent.md) | `__property TVerifyPeerEvent OnVerifyPeer;` |
| `OnBeforeBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnSocketAllocated: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAllocated;` |
| `OnWork: TWorkEvent` | [TWorkEvent](../types/TWorkEvent.md) | `__property TWorkEvent OnWork;` |
| `OnWorkBegin: TWorkBeginEvent` | [TWorkBeginEvent](../types/TWorkBeginEvent.md) | `__property TWorkBeginEvent OnWorkBegin;` |
| `OnWorkEnd: TWorkEndEvent` | [TWorkEndEvent](../types/TWorkEndEvent.md) | `__property TWorkEndEvent OnWorkEnd;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
function Clone: TIdSSLIOHandlerSocketBase;
procedure StartSSL;
procedure AfterAccept;
procedure Close;
procedure Open;
function Readable(AMSec: Integer = IdTimeoutDefault): Boolean;
function GetALPNProtocol: String;
function GetSSLVersion: String;
procedure CheckForDisconnect(ARaiseExceptionIfDisconnected: Boolean = True; AIgnoreBuffer: Boolean = False);
function Connected: Boolean;
function BindingAllocated: Boolean;
function WriteFile(const AFile: String; AEnableTransferFile: Boolean = False): Int64;
function CheckForDataOnSource(ATimeout: Integer = 0): Boolean;
procedure CloseGracefully;
class function MakeDefaultIOHandler(AOwner: TComponent = nil) : TIdIOHandler;
class function MakeIOHandler(ABaseType: TIdIOHandlerClass; AOwner: TComponent = nil): TIdIOHandler;
class function TryMakeIOHandler(ABaseType: TIdIOHandlerClass; AOwner: TComponent = nil): TIdIOHandler;
class procedure RegisterIOHandler;
class procedure SetDefaultClass;
function WaitFor(const AString: string; ARemoveFromBuffer: Boolean = True; AInclusive: Boolean = False; AByteEncoding: IIdTextEncoding = nil; ATimeout: Integer = IdTimeoutDefault ; AAnsiEncoding: IIdTextEncoding = nil ): string;
procedure Write(const ABuffer: TIdBytes; const ALength: Integer = -1; const AOffset: Integer = 0);
procedure WriteDirect(const ABuffer: TIdBytes; const ALength: Integer = -1; const AOffset: Integer = 0);
procedure WriteLn(AEncoding: IIdTextEncoding = nil);
procedure WriteLnRFC(const AOut: string = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure WriteRFCStrings(AStrings: TStrings; AWriteTerminator: Boolean = True; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
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

C++Builder

```cpp
TIdSSLIOHandlerSocketBase * __fastcall Clone();
void __fastcall StartSSL();
void __fastcall AfterAccept();
void __fastcall Close();
void __fastcall Open();
bool __fastcall Readable(int AMSec = IdTimeoutDefault);
UnicodeString __fastcall GetALPNProtocol();
UnicodeString __fastcall GetSSLVersion();
void __fastcall CheckForDisconnect(bool ARaiseExceptionIfDisconnected = True, bool AIgnoreBuffer = False);
bool __fastcall Connected();
bool __fastcall BindingAllocated();
long long __fastcall WriteFile(const UnicodeString AFile, bool AEnableTransferFile = False);
bool __fastcall CheckForDataOnSource(int ATimeout = 0);
void __fastcall CloseGracefully();
TIdIOHandler * __fastcall MakeDefaultIOHandler(TComponent * AOwner = nil);
TIdIOHandler * __fastcall MakeIOHandler(TIdIOHandlerClass * ABaseType, TComponent * AOwner = nil);
TIdIOHandler * __fastcall TryMakeIOHandler(TIdIOHandlerClass * ABaseType, TComponent * AOwner = nil);
void __fastcall RegisterIOHandler();
void __fastcall SetDefaultClass();
UnicodeString __fastcall WaitFor(const UnicodeString AString, bool ARemoveFromBuffer = True, bool AInclusive = False, IIdTextEncoding AByteEncoding = nil, int ATimeout = IdTimeoutDefault, IIdTextEncoding AAnsiEncoding = nil);
void __fastcall Write(const TIdBytes * ABuffer, const int ALength = -1, const int AOffset = 0);
void __fastcall WriteDirect(const TIdBytes * ABuffer, const int ALength = -1, const int AOffset = 0);
void __fastcall WriteLn(IIdTextEncoding AEncoding = nil);
void __fastcall WriteLnRFC(const UnicodeString AOut = '', IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
void __fastcall WriteRFCStrings(TStrings * AStrings, bool AWriteTerminator = True, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
UnicodeString __fastcall AllData(IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall InputLn(const UnicodeString AMask = '', bool AEcho = True, int ATabWidth = 8, int AMaxLineLength = -1, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding AAnsiEncoding = nil);
void __fastcall Capture(TStream * ADest, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall ReadBytes(TIdBytes * &VBuffer, int AByteCount, bool AAppend = True);
UnicodeString __fastcall ReadLn(IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall ReadLnRFC(bool &VMsgEnd, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall ReadLnWait(int AFailCount = MaxInt, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall ReadLnSplit(bool &AWasSplit, UnicodeString ATerminator = LF, int ATimeout = IdTimeoutDefault, int AMaxLineLength = -1, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
wchar_t __fastcall ReadChar(IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
unsigned char __fastcall ReadByte();
UnicodeString __fastcall ReadString(int ABytes, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
Int16 __fastcall ReadInt16(bool AConvert = True);
UInt16 __fastcall ReadUInt16(bool AConvert = True);
Int32 __fastcall ReadInt32(bool AConvert = True);
UInt32 __fastcall ReadUInt32(bool AConvert = True);
long long __fastcall ReadInt64(bool AConvert = True);
TIdUInt64 * __fastcall ReadUInt64(bool AConvert = True);
Int16 __fastcall ReadSmallInt(bool AConvert = True);
UInt16 __fastcall ReadWord(bool AConvert = True);
Int32 __fastcall ReadLongInt(bool AConvert = True);
UInt32 __fastcall ReadLongWord(bool AConvert = True);
void __fastcall ReadStream(TStream * AStream, TIdStreamSize * AByteCount = -1, bool AReadUntilDisconnect = False);
void __fastcall ReadStrings(TStrings * ADest, int AReadLinesCount = -1, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall Discard(long long AByteCount);
void __fastcall DiscardAll();
void __fastcall WriteBufferCancel();
void __fastcall WriteBufferClear();
void __fastcall WriteBufferClose();
void __fastcall WriteBufferFlush();
void __fastcall WriteBufferOpen();
bool __fastcall WriteBufferingActive();
bool __fastcall InputBufferIsEmpty();
void __fastcall InputBufferToStream(TStream * AStream, int AByteCount = -1);
UnicodeString __fastcall InputBufferAsString(IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

