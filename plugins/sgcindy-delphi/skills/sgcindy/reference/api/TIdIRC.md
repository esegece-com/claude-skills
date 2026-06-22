# TIdIRC

unit: IdIRC

Add `IdIRC` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Away: Boolean (read-only)` | `Boolean` | `__property bool Away /* read-only */;` |
| `SenderNick: String (read-only)` | `String` | `__property UnicodeString SenderNick /* read-only */;` |
| `SenderHost: String (read-only)` | `String` | `__property UnicodeString SenderHost /* read-only */;` |
| `Nickname: String` | `String` | `__property UnicodeString Nickname;` |
| `AltNickname: String` | `String` | `__property UnicodeString AltNickname;` |
| `UsedNickname: String (read-only)` | `String` | `__property UnicodeString UsedNickname /* read-only */;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `RealName: String` | `String` | `__property UnicodeString RealName;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `Replies: TIdIRCReplies` | `TIdIRCReplies` | `__property TIdIRCReplies * Replies;` |
| `UserMode: TIdIRCUserModes` | `TIdIRCUserModes` | `__property TIdIRCUserModes * UserMode;` |
| `CommandHandlers: TIdCommandHandlers` | [TIdCommandHandlers](../types/TIdCommandHandlers.md) | `__property TIdCommandHandlers * CommandHandlers;` |
| `ExceptionReply: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * ExceptionReply;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
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
| `OnServerWelcome: TIdIRCServerMsgEvent` | [TIdIRCServerMsgEvent](../types/TIdIRCServerMsgEvent.md) | `__property TIdIRCServerMsgEvent OnServerWelcome;` |
| `OnYourHost: TIdIRCServerMsgEvent` | [TIdIRCServerMsgEvent](../types/TIdIRCServerMsgEvent.md) | `__property TIdIRCServerMsgEvent OnYourHost;` |
| `OnServerCreated: TIdIRCServerMsgEvent` | [TIdIRCServerMsgEvent](../types/TIdIRCServerMsgEvent.md) | `__property TIdIRCServerMsgEvent OnServerCreated;` |
| `OnMyInfo: TIdIRCMyInfoEvent` | [TIdIRCMyInfoEvent](../types/TIdIRCMyInfoEvent.md) | `__property TIdIRCMyInfoEvent OnMyInfo;` |
| `OnBounce: TIdIRCBounceEvent` | [TIdIRCBounceEvent](../types/TIdIRCBounceEvent.md) | `__property TIdIRCBounceEvent OnBounce;` |
| `OnISupport: TIdIRCISupportEvent` | [TIdIRCISupportEvent](../types/TIdIRCISupportEvent.md) | `__property TIdIRCISupportEvent OnISupport;` |
| `OnPingPong: TIdIRCPingPongEvent` | [TIdIRCPingPongEvent](../types/TIdIRCPingPongEvent.md) | `__property TIdIRCPingPongEvent OnPingPong;` |
| `OnPrivateMessage: TIdIRCPrivMessageEvent` | [TIdIRCPrivMessageEvent](../types/TIdIRCPrivMessageEvent.md) | `__property TIdIRCPrivMessageEvent OnPrivateMessage;` |
| `OnNotice: TIdIRCNoticeEvent` | [TIdIRCNoticeEvent](../types/TIdIRCNoticeEvent.md) | `__property TIdIRCNoticeEvent OnNotice;` |
| `OnRehash: TIdIRCRehashEvent` | [TIdIRCRehashEvent](../types/TIdIRCRehashEvent.md) | `__property TIdIRCRehashEvent OnRehash;` |
| `OnSummon: TIdIRCSummonEvent` | [TIdIRCSummonEvent](../types/TIdIRCSummonEvent.md) | `__property TIdIRCSummonEvent OnSummon;` |
| `OnWallops: TIdIRCWallopsEvent` | [TIdIRCWallopsEvent](../types/TIdIRCWallopsEvent.md) | `__property TIdIRCWallopsEvent OnWallops;` |
| `OnIsOnIRC: TIdIRCIsOnIRCEvent` | [TIdIRCIsOnIRCEvent](../types/TIdIRCIsOnIRCEvent.md) | `__property TIdIRCIsOnIRCEvent OnIsOnIRC;` |
| `OnAway: TIdIRCAwayEvent` | [TIdIRCAwayEvent](../types/TIdIRCAwayEvent.md) | `__property TIdIRCAwayEvent OnAway;` |
| `OnJoin: TIdIRCJoinEvent` | [TIdIRCJoinEvent](../types/TIdIRCJoinEvent.md) | `__property TIdIRCJoinEvent OnJoin;` |
| `OnPart: TIdIRCPartEvent` | [TIdIRCPartEvent](../types/TIdIRCPartEvent.md) | `__property TIdIRCPartEvent OnPart;` |
| `OnTopic: TIdIRCTopicEvent` | [TIdIRCTopicEvent](../types/TIdIRCTopicEvent.md) | `__property TIdIRCTopicEvent OnTopic;` |
| `OnKick: TIdIRCKickEvent` | [TIdIRCKickEvent](../types/TIdIRCKickEvent.md) | `__property TIdIRCKickEvent OnKick;` |
| `OnMOTD: TIdIRCMOTDEvent` | [TIdIRCMOTDEvent](../types/TIdIRCMOTDEvent.md) | `__property TIdIRCMOTDEvent OnMOTD;` |
| `OnTrace: TIdIRCServerTraceEvent` | [TIdIRCServerTraceEvent](../types/TIdIRCServerTraceEvent.md) | `__property TIdIRCServerTraceEvent OnTrace;` |
| `OnOp: TIdIRCOpEvent` | [TIdIRCOpEvent](../types/TIdIRCOpEvent.md) | `__property TIdIRCOpEvent OnOp;` |
| `OnInviting: TIdIRCInvitingEvent` | [TIdIRCInvitingEvent](../types/TIdIRCInvitingEvent.md) | `__property TIdIRCInvitingEvent OnInviting;` |
| `OnInvite: TIdIRCInviteEvent` | [TIdIRCInviteEvent](../types/TIdIRCInviteEvent.md) | `__property TIdIRCInviteEvent OnInvite;` |
| `OnBanListReceived: TIdIRCChanBANListEvent` | [TIdIRCChanBANListEvent](../types/TIdIRCChanBANListEvent.md) | `__property TIdIRCChanBANListEvent OnBanListReceived;` |
| `OnExceptionListReceived: TIdIRCChanEXCListEvent` | [TIdIRCChanEXCListEvent](../types/TIdIRCChanEXCListEvent.md) | `__property TIdIRCChanEXCListEvent OnExceptionListReceived;` |
| `OnInvitationListReceived: TIdIRCChanINVListEvent` | [TIdIRCChanINVListEvent](../types/TIdIRCChanINVListEvent.md) | `__property TIdIRCChanINVListEvent OnInvitationListReceived;` |
| `OnServerListReceived: TIdIRCServerListEvent` | [TIdIRCServerListEvent](../types/TIdIRCServerListEvent.md) | `__property TIdIRCServerListEvent OnServerListReceived;` |
| `OnNicknamesListReceived: TIdIRCNickListEvent` | [TIdIRCNickListEvent](../types/TIdIRCNickListEvent.md) | `__property TIdIRCNickListEvent OnNicknamesListReceived;` |
| `OnServerUsersListReceived: TIdIRCServerUsersEvent` | [TIdIRCServerUsersEvent](../types/TIdIRCServerUsersEvent.md) | `__property TIdIRCServerUsersEvent OnServerUsersListReceived;` |
| `OnServerStatsReceived: TIdIRCServerStatsEvent` | [TIdIRCServerStatsEvent](../types/TIdIRCServerStatsEvent.md) | `__property TIdIRCServerStatsEvent OnServerStatsReceived;` |
| `OnKnownServersListReceived: TIdIRCKnownServerNamesEvent` | [TIdIRCKnownServerNamesEvent](../types/TIdIRCKnownServerNamesEvent.md) | `__property TIdIRCKnownServerNamesEvent OnKnownServersListReceived;` |
| `OnAdminInfoReceived: TIdIRCAdminInfoRecvEvent` | [TIdIRCAdminInfoRecvEvent](../types/TIdIRCAdminInfoRecvEvent.md) | `__property TIdIRCAdminInfoRecvEvent OnAdminInfoReceived;` |
| `OnUserInfoReceived: TIdIRCUserInfoRecvEvent` | [TIdIRCUserInfoRecvEvent](../types/TIdIRCUserInfoRecvEvent.md) | `__property TIdIRCUserInfoRecvEvent OnUserInfoReceived;` |
| `OnWho: TIdIRCWhoEvent` | [TIdIRCWhoEvent](../types/TIdIRCWhoEvent.md) | `__property TIdIRCWhoEvent OnWho;` |
| `OnWhoIs: TIdIRCWhoIsEvent` | [TIdIRCWhoIsEvent](../types/TIdIRCWhoIsEvent.md) | `__property TIdIRCWhoIsEvent OnWhoIs;` |
| `OnWhoWas: TIdIRCWhoWasEvent` | [TIdIRCWhoWasEvent](../types/TIdIRCWhoWasEvent.md) | `__property TIdIRCWhoWasEvent OnWhoWas;` |
| `OnChannelMode: TIdIRCChanModeEvent` | [TIdIRCChanModeEvent](../types/TIdIRCChanModeEvent.md) | `__property TIdIRCChanModeEvent OnChannelMode;` |
| `OnUserMode: TIdIRCUserModeEvent` | [TIdIRCUserModeEvent](../types/TIdIRCUserModeEvent.md) | `__property TIdIRCUserModeEvent OnUserMode;` |
| `OnCTCPQuery: TIdIRCCTCPQueryEvent` | [TIdIRCCTCPQueryEvent](../types/TIdIRCCTCPQueryEvent.md) | `__property TIdIRCCTCPQueryEvent OnCTCPQuery;` |
| `OnCTCPReply: TIdIRCCTCPReplyEvent` | [TIdIRCCTCPReplyEvent](../types/TIdIRCCTCPReplyEvent.md) | `__property TIdIRCCTCPReplyEvent OnCTCPReply;` |
| `OnDCCChat: TIdIRCDCCChatEvent` | [TIdIRCDCCChatEvent](../types/TIdIRCDCCChatEvent.md) | `__property TIdIRCDCCChatEvent OnDCCChat;` |
| `OnDCCSend: TIdIRCDCCSendEvent` | [TIdIRCDCCSendEvent](../types/TIdIRCDCCSendEvent.md) | `__property TIdIRCDCCSendEvent OnDCCSend;` |
| `OnDCCResume: TIdIRCDCCResumeEvent` | [TIdIRCDCCResumeEvent](../types/TIdIRCDCCResumeEvent.md) | `__property TIdIRCDCCResumeEvent OnDCCResume;` |
| `OnDCCAccept: TIdIRCDCCAcceptEvent` | [TIdIRCDCCAcceptEvent](../types/TIdIRCDCCAcceptEvent.md) | `__property TIdIRCDCCAcceptEvent OnDCCAccept;` |
| `OnServerError: TIdIRCServerErrorEvent` | [TIdIRCServerErrorEvent](../types/TIdIRCServerErrorEvent.md) | `__property TIdIRCServerErrorEvent OnServerError;` |
| `OnNicknameError: TIdIRCNickErrorEvent` | [TIdIRCNickErrorEvent](../types/TIdIRCNickErrorEvent.md) | `__property TIdIRCNickErrorEvent OnNicknameError;` |
| `OnKillError: TIdIRCKillErrorEvent` | [TIdIRCKillErrorEvent](../types/TIdIRCKillErrorEvent.md) | `__property TIdIRCKillErrorEvent OnKillError;` |
| `OnNicknameChange: TIdIRCNicknameChangedEvent` | [TIdIRCNicknameChangedEvent](../types/TIdIRCNicknameChangedEvent.md) | `__property TIdIRCNicknameChangedEvent OnNicknameChange;` |
| `OnKill: TIdIRCKillEvent` | [TIdIRCKillEvent](../types/TIdIRCKillEvent.md) | `__property TIdIRCKillEvent OnKill;` |
| `OnQuit: TIdIRCQuitEvent` | [TIdIRCQuitEvent](../types/TIdIRCQuitEvent.md) | `__property TIdIRCQuitEvent OnQuit;` |
| `OnServerQuit: TIdIRCSvrQuitEvent` | [TIdIRCSvrQuitEvent](../types/TIdIRCSvrQuitEvent.md) | `__property TIdIRCSvrQuitEvent OnServerQuit;` |
| `OnServerTime: TIdIRCSvrTimeEvent` | [TIdIRCSvrTimeEvent](../types/TIdIRCSvrTimeEvent.md) | `__property TIdIRCSvrTimeEvent OnServerTime;` |
| `OnService: TIdIRCServiceEvent` | [TIdIRCServiceEvent](../types/TIdIRCServiceEvent.md) | `__property TIdIRCServiceEvent OnService;` |
| `OnServerVersion: TIdIRCSvrVersionEvent` | [TIdIRCSvrVersionEvent](../types/TIdIRCSvrVersionEvent.md) | `__property TIdIRCSvrVersionEvent OnServerVersion;` |
| `OnRaw: TIdIRCRawEvent` | [TIdIRCRawEvent](../types/TIdIRCRawEvent.md) | `__property TIdIRCRawEvent OnRaw;` |
| `OnAfterCommandHandler: TIdCmdTCPClientAfterCommandHandlerEvent` | [TIdCmdTCPClientAfterCommandHandlerEvent](../types/TIdCmdTCPClientAfterCommandHandlerEvent.md) | `__property TIdCmdTCPClientAfterCommandHandlerEvent OnAfterCommandHandler;` |
| `OnBeforeCommandHandler: TIdCmdTCPClientBeforeCommandHandlerEvent` | [TIdCmdTCPClientBeforeCommandHandlerEvent](../types/TIdCmdTCPClientBeforeCommandHandlerEvent.md) | `__property TIdCmdTCPClientBeforeCommandHandlerEvent OnBeforeCommandHandler;` |
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
procedure Connect;
procedure Disconnect(const AReason: String = '');
function IsChannel(const AChannel: String): Boolean;
function IsOp(const ANickname: String): Boolean;
function IsVoice(const ANickname: String): Boolean;
procedure Raw(const ALine: String);
procedure Say(const ATarget, AMsg: String);
procedure Notice(const ATarget, AMsg: String);
procedure Action(const ATarget, AMsg: String);
procedure CTCPQuery(const ATarget, ACommand, AParameters: String);
procedure CTCPReply(const ATarget, ACTCP, AReply: String);
procedure Join(const AChannel: String; const AKey: String ='');
procedure Part(const AChannel: String; const AReason: String = '');
procedure Kick(const AChannel, ANickname: String; const AReason: String = '');
procedure SetChannelMode(const AChannel, AMode: String; const AParams: String = '');
procedure SetUserMode(const ANickname, AMode: String);
procedure GetChannelTopic(const AChannel: String);
procedure SetChannelTopic(const AChannel, ATopic: String);
procedure SetAway(const AMsg: String);
procedure Op(const AChannel, ANickname: String);
procedure Deop(const AChannel, ANickname: String);
procedure Voice(const AChannel, ANickname: String);
procedure Devoice(const AChannel, ANickname: String);
procedure Ban(const AChannel, AHostmask: String);
procedure Unban(const AChannel, AHostmask: String);
procedure RegisterService(const ANickname, ADistribution, AInfo: String; AType: Integer);
procedure ListChannelNicknames(const AChannel: String; const ATarget: String = '');
procedure ListChannel(const AChannel: String; const ATarget: String = '');
procedure Invite(const ANickname, AChannel: String);
procedure GetMessageOfTheDay(const ATarget: String = '');
procedure GetNetworkStatus(const AHostMask: String = ''; const ATarget: String = '');
procedure GetServerVersion(const ATarget: String = '');
procedure GetServerStatus(AQuery: TIdIRCStat; const ATarget: String = '');
procedure ListKnownServerNames(const ARemoteHost: String = ''; const AHostMask: String = '');
procedure QueryServerTime(const ATarget: String = '');
procedure RequestServerConnect(const ATargetHost: String; APort: Integer; const ARemoteHost: String = '');
procedure TraceServer(const ATarget: String = '');
procedure GetAdminInfo(const ATarget: String = '');
procedure GetServerInfo(const ATarget: String = '');
procedure ListNetworkServices(const AHostMask: String = ''; const AType: String = '');
procedure QueryService(const AServiceName, AMessage: String);
procedure Who(const AMask: String; AOnlyAdmins: Boolean);
procedure WhoIs(const AMask: String; const ATarget: String = '');
procedure WhoWas(const ANickname: String; ACount: Integer = -1; const ATarget: String = '');
procedure Kill(const ANickname, AComment: String);
procedure Ping(const AServer1: String; const AServer2: String = '');
procedure Pong(const AServer1: String; const AServer2: String = '');
procedure Error(const AMessage: String);
procedure ReHash;
procedure Die;
procedure Restart;
procedure Summon(const ANickname: String; const ATarget: String = ''; const AChannel: String = '');
procedure ListServerUsers(const ATarget: String = '');
procedure SayWALLOPS(const AMessage: String);
procedure GetUserInfo(const ANickname: String);
procedure GetUsersInfo(const ANicknames: array of String);
procedure IsOnIRC(const ANickname: String);
procedure BecomeOp(const ANickname, APassword: String);
procedure SQuit(const AHost, AComment: String);
procedure SetChannelLimit(const AChannel: String; ALimit: Integer);
procedure SetChannelKey(const AChannel, AKey: String);
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function Connected: Boolean;
procedure DisconnectNotifyPeer;
procedure GetInternalResponse(AEncoding: IIdTextEncoding = nil);
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
void __fastcall Connect();
void __fastcall Disconnect(const UnicodeString AReason = '');
bool __fastcall IsChannel(const UnicodeString AChannel);
bool __fastcall IsOp(const UnicodeString ANickname);
bool __fastcall IsVoice(const UnicodeString ANickname);
void __fastcall Raw(const UnicodeString ALine);
void __fastcall Say(const UnicodeString ATarget, const UnicodeString AMsg);
void __fastcall Notice(const UnicodeString ATarget, const UnicodeString AMsg);
void __fastcall Action(const UnicodeString ATarget, const UnicodeString AMsg);
void __fastcall CTCPQuery(const UnicodeString ATarget, const UnicodeString ACommand, const UnicodeString AParameters);
void __fastcall CTCPReply(const UnicodeString ATarget, const UnicodeString ACTCP, const UnicodeString AReply);
void __fastcall Join(const UnicodeString AChannel, const UnicodeString AKey = '');
void __fastcall Part(const UnicodeString AChannel, const UnicodeString AReason = '');
void __fastcall Kick(const UnicodeString AChannel, const UnicodeString ANickname, const UnicodeString AReason = '');
void __fastcall SetChannelMode(const UnicodeString AChannel, const UnicodeString AMode, const UnicodeString AParams = '');
void __fastcall SetUserMode(const UnicodeString ANickname, const UnicodeString AMode);
void __fastcall GetChannelTopic(const UnicodeString AChannel);
void __fastcall SetChannelTopic(const UnicodeString AChannel, const UnicodeString ATopic);
void __fastcall SetAway(const UnicodeString AMsg);
void __fastcall Op(const UnicodeString AChannel, const UnicodeString ANickname);
void __fastcall Deop(const UnicodeString AChannel, const UnicodeString ANickname);
void __fastcall Voice(const UnicodeString AChannel, const UnicodeString ANickname);
void __fastcall Devoice(const UnicodeString AChannel, const UnicodeString ANickname);
void __fastcall Ban(const UnicodeString AChannel, const UnicodeString AHostmask);
void __fastcall Unban(const UnicodeString AChannel, const UnicodeString AHostmask);
void __fastcall RegisterService(const UnicodeString ANickname, const UnicodeString ADistribution, const UnicodeString AInfo, int AType);
void __fastcall ListChannelNicknames(const UnicodeString AChannel, const UnicodeString ATarget = '');
void __fastcall ListChannel(const UnicodeString AChannel, const UnicodeString ATarget = '');
void __fastcall Invite(const UnicodeString ANickname, const UnicodeString AChannel);
void __fastcall GetMessageOfTheDay(const UnicodeString ATarget = '');
void __fastcall GetNetworkStatus(const UnicodeString AHostMask = '', const UnicodeString ATarget = '');
void __fastcall GetServerVersion(const UnicodeString ATarget = '');
void __fastcall GetServerStatus(TIdIRCStat * AQuery, const UnicodeString ATarget = '');
void __fastcall ListKnownServerNames(const UnicodeString ARemoteHost = '', const UnicodeString AHostMask = '');
void __fastcall QueryServerTime(const UnicodeString ATarget = '');
void __fastcall RequestServerConnect(const UnicodeString ATargetHost, int APort, const UnicodeString ARemoteHost = '');
void __fastcall TraceServer(const UnicodeString ATarget = '');
void __fastcall GetAdminInfo(const UnicodeString ATarget = '');
void __fastcall GetServerInfo(const UnicodeString ATarget = '');
void __fastcall ListNetworkServices(const UnicodeString AHostMask = '', const UnicodeString AType = '');
void __fastcall QueryService(const UnicodeString AServiceName, const UnicodeString AMessage);
void __fastcall Who(const UnicodeString AMask, bool AOnlyAdmins);
void __fastcall WhoIs(const UnicodeString AMask, const UnicodeString ATarget = '');
void __fastcall WhoWas(const UnicodeString ANickname, int ACount = -1, const UnicodeString ATarget = '');
void __fastcall Kill(const UnicodeString ANickname, const UnicodeString AComment);
void __fastcall Ping(const UnicodeString AServer1, const UnicodeString AServer2 = '');
void __fastcall Pong(const UnicodeString AServer1, const UnicodeString AServer2 = '');
void __fastcall Error(const UnicodeString AMessage);
void __fastcall ReHash();
void __fastcall Die();
void __fastcall Restart();
void __fastcall Summon(const UnicodeString ANickname, const UnicodeString ATarget = '', const UnicodeString AChannel = '');
void __fastcall ListServerUsers(const UnicodeString ATarget = '');
void __fastcall SayWALLOPS(const UnicodeString AMessage);
void __fastcall GetUserInfo(const UnicodeString ANickname);
void __fastcall GetUsersInfo(const array of String ANicknames);
void __fastcall IsOnIRC(const UnicodeString ANickname);
void __fastcall BecomeOp(const UnicodeString ANickname, const UnicodeString APassword);
void __fastcall SQuit(const UnicodeString AHost, const UnicodeString AComment);
void __fastcall SetChannelLimit(const UnicodeString AChannel, int ALimit);
void __fastcall SetChannelKey(const UnicodeString AChannel, const UnicodeString AKey);
UnicodeString __fastcall ConnectAndGetAll();
void __fastcall CreateIOHandler(TIdIOHandlerClass * ABaseType = nil);
void __fastcall CheckForGracefulDisconnect(bool ARaiseExceptionIfDisconnected = True);
Int16 __fastcall CheckResponse(const Int16 AResponse, const array of Int16 AAllowedResponses);
bool __fastcall Connected();
void __fastcall DisconnectNotifyPeer();
void __fastcall GetInternalResponse(IIdTextEncoding AEncoding = nil);
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

