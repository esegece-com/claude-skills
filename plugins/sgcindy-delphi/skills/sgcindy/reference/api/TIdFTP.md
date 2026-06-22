# TIdFTP

unit: IdFTP

Add `IdFTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `IsCompressionSupported: Boolean (read-only)` | `Boolean` | `__property bool IsCompressionSupported /* read-only */;` |
| `SupportsVerification: Boolean (read-only)` | `Boolean` | `__property bool SupportsVerification /* read-only */;` |
| `CanResume: Boolean (read-only)` | `Boolean` | `__property bool CanResume /* read-only */;` |
| `CanUseMLS: Boolean (read-only)` | `Boolean` | `__property bool CanUseMLS /* read-only */;` |
| `DirectoryListing: TIdFTPListItems (read-only)` | [TIdFTPListItems](../types/TIdFTPListItems.md) | `__property TIdFTPListItems * DirectoryListing /* read-only */;` |
| `DirFormat: String (read-only)` | `String` | `__property UnicodeString DirFormat /* read-only */;` |
| `LangsSupported: TStrings (read-only)` | `TStrings` | `__property TStrings * LangsSupported /* read-only */;` |
| `ListParserClass: TIdFTPListParseClass` | [TIdFTPListParseClass](../types/TIdFTPListParseClass.md) | `__property TIdFTPListParseClass * ListParserClass;` |
| `LoginMsg: TIdReplyFTP (read-only)` | [TIdReplyFTP](../types/TIdReplyFTP.md) | `__property TIdReplyFTP * LoginMsg /* read-only */;` |
| `ListResult: TStrings (read-only)` | `TStrings` | `__property TStrings * ListResult /* read-only */;` |
| `SystemDesc: string (read-only)` | `string` | `__property UnicodeString SystemDesc /* read-only */;` |
| `TZInfo: TIdFTPTZInfo` | [TIdFTPTZInfo](../types/TIdFTPTZInfo.md) | `__property TIdFTPTZInfo * TZInfo;` |
| `UsingExtDataPort: Boolean (read-only)` | `Boolean` | `__property bool UsingExtDataPort /* read-only */;` |
| `UsingNATFastTrack: Boolean (read-only)` | `Boolean` | `__property bool UsingNATFastTrack /* read-only */;` |
| `UsingSFTP: Boolean (read-only)` | `Boolean` | `__property bool UsingSFTP /* read-only */;` |
| `CurrentTransferMode: TIdFTPTransferMode` | [TIdFTPTransferMode](../types/TIdFTPTransferMode.md) | `__property TIdFTPTransferMode * CurrentTransferMode;` |
| `DefStringEncoding: IIdTextEncoding` | [IIdTextEncoding](../types/IIdTextEncoding.md) | `__property IIdTextEncoding DefStringEncoding;` |
| `ServerInfo: TIdFTPServerIdentifier (read-only)` | [TIdFTPServerIdentifier](../types/TIdFTPServerIdentifier.md) | `__property TIdFTPServerIdentifier * ServerInfo /* read-only */;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `AutoIssueFEAT: Boolean` | `Boolean` | `__property bool AutoIssueFEAT;` |
| `AutoLogin: Boolean` | `Boolean` | `__property bool AutoLogin;` |
| `Compressor: TIdZLibCompressorBase` | [TIdZLibCompressorBase](../types/TIdZLibCompressorBase.md) | `__property TIdZLibCompressorBase * Compressor;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `UseCCC: Boolean` | `Boolean` | `__property bool UseCCC;` |
| `Passive: boolean` | `boolean` | `__property bool Passive;` |
| `PassiveUseControlHost: Boolean` | `Boolean` | `__property bool PassiveUseControlHost;` |
| `DataPortProtection: TIdFTPDataPortSecurity` | [TIdFTPDataPortSecurity](../types/TIdFTPDataPortSecurity.md) | `__property TIdFTPDataPortSecurity * DataPortProtection;` |
| `AUTHCmd: TAuthCmd` | [TAuthCmd](../types/TAuthCmd.md) | `__property TAuthCmd * AUTHCmd;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `DataPort: TIdPort` | `TIdPort` | `__property TIdPort * DataPort;` |
| `DataPortMin: TIdPort` | `TIdPort` | `__property TIdPort * DataPortMin;` |
| `DataPortMax: TIdPort` | `TIdPort` | `__property TIdPort * DataPortMax;` |
| `ExternalIP: String` | `String` | `__property UnicodeString ExternalIP;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `TransferType: TIdFTPTransferType` | [TIdFTPTransferType](../types/TIdFTPTransferType.md) | `__property TIdFTPTransferType * TransferType;` |
| `TransferTimeout: Integer` | `Integer` | `__property int TransferTimeout;` |
| `ListenTimeout: Integer` | `Integer` | `__property int ListenTimeout;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `UseExtensionDataPort: Boolean` | `Boolean` | `__property bool UseExtensionDataPort;` |
| `UseMLIS: Boolean` | `Boolean` | `__property bool UseMLIS;` |
| `TryNATFastTrack: Boolean` | `Boolean` | `__property bool TryNATFastTrack;` |
| `NATKeepAlive: TIdFTPKeepAlive` | [TIdFTPKeepAlive](../types/TIdFTPKeepAlive.md) | `__property TIdFTPKeepAlive * NATKeepAlive;` |
| `ProxySettings: TIdFtpProxySettings` | [TIdFtpProxySettings](../types/TIdFtpProxySettings.md) | `__property TIdFtpProxySettings * ProxySettings;` |
| `Account: string` | `string` | `__property UnicodeString Account;` |
| `ClientInfo: TIdFTPClientIdentifier` | [TIdFTPClientIdentifier](../types/TIdFTPClientIdentifier.md) | `__property TIdFTPClientIdentifier * ClientInfo;` |
| `UseHOST: Boolean` | `Boolean` | `__property bool UseHOST;` |
| `ServerHOST: String` | `String` | `__property UnicodeString ServerHOST;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `SupportsTLS: boolean (read-only)` | `boolean` | `__property bool SupportsTLS /* read-only */;` |
| `Capabilities: TStrings (read-only)` | `TStrings` | `__property TStrings * Capabilities /* read-only */;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `LingerState: Integer` | `Integer` | `__property int LingerState;` |
| `Greeting: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * Greeting;` |
| `LastCmdResult: TIdReply (read-only)` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * LastCmdResult /* read-only */;` |
| `ManagedIOHandler: Boolean` | `Boolean` | `__property bool ManagedIOHandler;` |
| `Socket: TIdIOHandlerSocket (read-only)` | [TIdIOHandlerSocket](../types/TIdIOHandlerSocket.md) | `__property TIdIOHandlerSocket * Socket /* read-only */;` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](../types/TIdConnectionIntercept.md) | `__property TIdConnectionIntercept * Intercept;` |
| `IOHandler: TIdIOHandler` | [TIdIOHandler](../types/TIdIOHandler.md) | `__property TIdIOHandler * IOHandler;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnTLSNotAvailable: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNotAvailable;` |
| `OnBannerBeforeLogin: TIdFTPBannerEvent` | [TIdFTPBannerEvent](../types/TIdFTPBannerEvent.md) | `__property TIdFTPBannerEvent OnBannerBeforeLogin;` |
| `OnBannerAfterLogin: TIdFTPBannerEvent` | [TIdFTPBannerEvent](../types/TIdFTPBannerEvent.md) | `__property TIdFTPBannerEvent OnBannerAfterLogin;` |
| `OnBannerWarning: TIdFTPBannerEvent` | [TIdFTPBannerEvent](../types/TIdFTPBannerEvent.md) | `__property TIdFTPBannerEvent OnBannerWarning;` |
| `OnBeforeGet: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeGet;` |
| `OnBeforePut: TIdFtpAfterGet` | [TIdFtpAfterGet](../types/TIdFtpAfterGet.md) | `__property TIdFtpAfterGet * OnBeforePut;` |
| `OnAfterClientLogin: TOnAfterClientLogin` | `TOnAfterClientLogin` | `__property TOnAfterClientLogin OnAfterClientLogin;` |
| `OnCreateFTPList: TIdCreateFTPList` | [TIdCreateFTPList](../types/TIdCreateFTPList.md) | `__property TIdCreateFTPList * OnCreateFTPList;` |
| `OnAfterGet: TIdFtpAfterGet` | [TIdFtpAfterGet](../types/TIdFtpAfterGet.md) | `__property TIdFtpAfterGet * OnAfterGet;` |
| `OnAfterPut: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterPut;` |
| `OnNeedAccount: TIdNeedAccountEvent` | [TIdNeedAccountEvent](../types/TIdNeedAccountEvent.md) | `__property TIdNeedAccountEvent OnNeedAccount;` |
| `OnCustomFTPProxy: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnCustomFTPProxy;` |
| `OnDataChannelCreate: TIdOnDataChannelCreate` | [TIdOnDataChannelCreate](../types/TIdOnDataChannelCreate.md) | `__property TIdOnDataChannelCreate * OnDataChannelCreate;` |
| `OnDataChannelDestroy: TIdOnDataChannelDestroy` | [TIdOnDataChannelDestroy](../types/TIdOnDataChannelDestroy.md) | `__property TIdOnDataChannelDestroy * OnDataChannelDestroy;` |
| `OnRetrievedDir: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnRetrievedDir;` |
| `OnDirParseStart: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDirParseStart;` |
| `OnDirParseEnd: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDirParseEnd;` |
| `OnTLSHandShakeFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSHandShakeFailed;` |
| `OnTLSNegCmdFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNegCmdFailed;` |
| `OnBeforeBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnSocketAllocated: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAllocated;` |
| `OnConnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnConnected;` |
| `OnDisconnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnected;` |
| `OnWork: TWorkEvent` | [TWorkEvent](../types/TWorkEvent.md) | `__property TWorkEvent OnWork;` |
| `OnWorkBegin: TWorkBeginEvent` | [TWorkBeginEvent](../types/TWorkBeginEvent.md) | `__property TWorkBeginEvent OnWorkBegin;` |
| `OnWorkEnd: TWorkEndEvent` | [TWorkEndEvent](../types/TWorkEndEvent.md) | `__property TWorkEndEvent OnWorkEnd;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure GetInternalResponse(AEncoding: IIdTextEncoding = nil);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function IsExtSupported(const ACmd : String):Boolean;
procedure ExtractFeatFacts(const ACmd : String; AResults : TStrings);
function GetLoginPassword : String;
procedure Abort;
procedure Allocate(AAllocateBytes: Integer);
procedure ChangeDir(const ADirName: string);
procedure ChangeDirUp;
procedure Connect;
procedure Delete(const AFilename: string);
procedure FileStructure(AStructure: TIdFTPDataStructure);
procedure Get(const ASourceFile: string; ADest: TStream; AResume: Boolean = false);
procedure Help(AHelpContents: TStrings; ACommand: String = '');
procedure KillDataChannel;
procedure List;
procedure ExtListDir(ADest: TStrings = nil; const ADirectory: string = '');
procedure ExtListItem(ADest: TStrings; AFList : TIdFTPListItems; const AItem: string='');
function FileDate(const AFileName : String; const AsGMT : Boolean = False): TDateTime;
procedure Login;
procedure MakeDir(const ADirName: string);
procedure Noop;
procedure SetCmdOpt(const ACMD, AOptions : String);
procedure Put(const ASource: TStream; const ADestFile: string; const AAppend: Boolean = False; const AStartPos: TIdStreamSize = -1);
procedure StoreUnique(const ASource: TStream; const AStartPos: TIdStreamSize = -1);
procedure SiteToSiteUpload(const AToSite : TIdFTP; const ASourceFile : String; const ADestFile : String = '');
procedure SiteToSiteDownload(const AFromSite: TIdFTP; const ASourceFile : String; const ADestFile : String = '');
procedure DisconnectNotifyPeer;
procedure Quit;
function Quote(const ACommand: String): Int16;
procedure RemoveDir(const ADirName: string);
procedure Rename(const ASourceFile, ADestFile: string);
function ResumeSupported: Boolean;
function RetrieveCurrentDir: string;
procedure Site(const ACommand: string);
function Size(const AFileName: String): Int64;
procedure Status(AStatusList: TStrings);
procedure StructureMount(APath: String);
procedure TransferMode(ATransferMode: TIdFTPTransferMode);
procedure ReInitialize(ADelay: UInt32 = 10);
procedure SetLang(const ALangTag : String);
function CRC(const AFIleName : String; const AStartPoint : Int64 = 0; const AEndPoint : Int64=0) : Int64;
function VerifyFile(ALocalFile : TStream; const ARemoteFile : String; const AStartPoint : TIdStreamSize = 0; const AByteCount : TIdStreamSize = 0) : Boolean;
procedure CombineFiles(const ATargetFile : String; AFileParts : TStrings);
procedure SetModTime(const AFileName: String; const ALocalTime: TDateTime);
procedure SetModTimeGMT(const AFileName : String; const AGMTTime: TDateTime);
function IsServerMDTZAndListTForm : Boolean;
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function Connected: Boolean;
procedure Disconnect;
function GetResponse(const AAllowedResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure RaiseExceptionForLastCmdResult;
function SendCmd(AOut: string; const AResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure WriteHeader(AHeader: TStrings);
procedure WriteRFCStrings(AStrings: TStrings);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall GetInternalResponse(IIdTextEncoding AEncoding = nil);
Int16 __fastcall CheckResponse(const Int16 AResponse, const array of Int16 AAllowedResponses);
bool __fastcall IsExtSupported(const UnicodeString ACmd);
void __fastcall ExtractFeatFacts(const UnicodeString ACmd, TStrings * AResults);
UnicodeString __fastcall GetLoginPassword();
void __fastcall Abort();
void __fastcall Allocate(int AAllocateBytes);
void __fastcall ChangeDir(const UnicodeString ADirName);
void __fastcall ChangeDirUp();
void __fastcall Connect();
void __fastcall Delete(const UnicodeString AFilename);
void __fastcall FileStructure(TIdFTPDataStructure * AStructure);
void __fastcall Get(const UnicodeString ASourceFile, TStream * ADest, bool AResume = false);
void __fastcall Help(TStrings * AHelpContents, UnicodeString ACommand = '');
void __fastcall KillDataChannel();
void __fastcall List();
void __fastcall ExtListDir(TStrings * ADest = nil, const UnicodeString ADirectory = '');
void __fastcall ExtListItem(TStrings * ADest, TIdFTPListItems * AFList, const UnicodeString AItem = '');
System::TDateTime __fastcall FileDate(const UnicodeString AFileName, const bool AsGMT = False);
void __fastcall Login();
void __fastcall MakeDir(const UnicodeString ADirName);
void __fastcall Noop();
void __fastcall SetCmdOpt(const UnicodeString ACMD, const UnicodeString AOptions);
void __fastcall Put(const TStream * ASource, const UnicodeString ADestFile, const bool AAppend = False, const TIdStreamSize * AStartPos = -1);
void __fastcall StoreUnique(const TStream * ASource, const TIdStreamSize * AStartPos = -1);
void __fastcall SiteToSiteUpload(const TIdFTP * AToSite, const UnicodeString ASourceFile, const UnicodeString ADestFile = '');
void __fastcall SiteToSiteDownload(const TIdFTP * AFromSite, const UnicodeString ASourceFile, const UnicodeString ADestFile = '');
void __fastcall DisconnectNotifyPeer();
void __fastcall Quit();
Int16 __fastcall Quote(const UnicodeString ACommand);
void __fastcall RemoveDir(const UnicodeString ADirName);
void __fastcall Rename(const UnicodeString ASourceFile, const UnicodeString ADestFile);
bool __fastcall ResumeSupported();
UnicodeString __fastcall RetrieveCurrentDir();
void __fastcall Site(const UnicodeString ACommand);
long long __fastcall Size(const UnicodeString AFileName);
void __fastcall Status(TStrings * AStatusList);
void __fastcall StructureMount(UnicodeString APath);
void __fastcall TransferMode(TIdFTPTransferMode * ATransferMode);
void __fastcall ReInitialize(UInt32 ADelay = 10);
void __fastcall SetLang(const UnicodeString ALangTag);
long long __fastcall CRC(const UnicodeString AFIleName, const long long AStartPoint = 0, const long long AEndPoint = 0);
bool __fastcall VerifyFile(TStream * ALocalFile, const UnicodeString ARemoteFile, const TIdStreamSize * AStartPoint = 0, const TIdStreamSize * AByteCount = 0);
void __fastcall CombineFiles(const UnicodeString ATargetFile, TStrings * AFileParts);
void __fastcall SetModTime(const UnicodeString AFileName, const System::TDateTime ALocalTime);
void __fastcall SetModTimeGMT(const UnicodeString AFileName, const System::TDateTime AGMTTime);
bool __fastcall IsServerMDTZAndListTForm();
UnicodeString __fastcall ConnectAndGetAll();
void __fastcall CreateIOHandler(TIdIOHandlerClass * ABaseType = nil);
void __fastcall CheckForGracefulDisconnect(bool ARaiseExceptionIfDisconnected = True);
bool __fastcall Connected();
void __fastcall Disconnect();
Int16 __fastcall GetResponse(const Int16 AAllowedResponse = -1, IIdTextEncoding AEncoding = nil);
void __fastcall RaiseExceptionForLastCmdResult();
Int16 __fastcall SendCmd(UnicodeString AOut, const Int16 AResponse = -1, IIdTextEncoding AEncoding = nil);
void __fastcall WriteHeader(TStrings * AHeader);
void __fastcall WriteRFCStrings(TStrings * AStrings);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

