# TsgcWSPServer_Presence

unit: sgcWebSocket_Protocols
Edition: Professional

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Acknowledgment: TsgcWSAckClient_Options` | [TsgcWSAckClient_Options](../types/TsgcWSAckClient_Options.md) | `__property TsgcWSAckClient_Options * Acknowledgment;` |
| `EncodeBase64: Boolean` | `Boolean` | `__property bool EncodeBase64;` |
| `Server: TsgcWSHTTPServer` | [TsgcWSHTTPServer](../types/TsgcWSHTTPServer.md) | `__property TsgcWSHTTPServer * Server;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](../types/TsgcHTTP2ClientConnectEvent.md) | `__property TsgcHTTP2ClientConnectEvent OnConnect;` |
| `OnDisconnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnect;` |
| `OnError: TsgcHTTP3ErrorEvent` | `TsgcHTTP3ErrorEvent` | `__property TsgcHTTP3ErrorEvent OnError;` |
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnException: TsgcAMQP1OnExceptionEvent` | [TsgcAMQP1OnExceptionEvent](../types/TsgcAMQP1OnExceptionEvent.md) | `__property TsgcAMQP1OnExceptionEvent OnException;` |
| `OnBeforeNewMember: TsgcWSPresenceBeforeNewMember` | [TsgcWSPresenceBeforeNewMember](../types/TsgcWSPresenceBeforeNewMember.md) | `__property TsgcWSPresenceBeforeNewMember * OnBeforeNewMember;` |
| `OnNewMember: TsgcWSPresenceNewMemberEvent` | [TsgcWSPresenceNewMemberEvent](../types/TsgcWSPresenceNewMemberEvent.md) | `__property TsgcWSPresenceNewMemberEvent OnNewMember;` |
| `OnRemoveMember: TsgcWSPresenceRemoveMemberEvent` | [TsgcWSPresenceRemoveMemberEvent](../types/TsgcWSPresenceRemoveMemberEvent.md) | `__property TsgcWSPresenceRemoveMemberEvent OnRemoveMember;` |
| `OnBeforeNewChannel: TsgcWSPresenceBeforeNewChannel` | [TsgcWSPresenceBeforeNewChannel](../types/TsgcWSPresenceBeforeNewChannel.md) | `__property TsgcWSPresenceBeforeNewChannel * OnBeforeNewChannel;` |
| `OnNewChannel: TsgcWSPresenceNewChannel` | [TsgcWSPresenceNewChannel](../types/TsgcWSPresenceNewChannel.md) | `__property TsgcWSPresenceNewChannel * OnNewChannel;` |
| `OnBeforeNewChannelMember: TsgcWSPresenceBeforeNewMemberChannel` | [TsgcWSPresenceBeforeNewMemberChannel](../types/TsgcWSPresenceBeforeNewMemberChannel.md) | `__property TsgcWSPresenceBeforeNewMemberChannel * OnBeforeNewChannelMember;` |
| `OnNewChannelMember: TsgcWSPresenceNewMemberChannelEvent` | [TsgcWSPresenceNewMemberChannelEvent](../types/TsgcWSPresenceNewMemberChannelEvent.md) | `__property TsgcWSPresenceNewMemberChannelEvent OnNewChannelMember;` |
| `OnRemoveChannelMember: TsgcWSPresenceRemoveMemberChannelEvent` | [TsgcWSPresenceRemoveMemberChannelEvent](../types/TsgcWSPresenceRemoveMemberChannelEvent.md) | `__property TsgcWSPresenceRemoveMemberChannelEvent OnRemoveChannelMember;` |
| `OnBeforePublishMsg: TsgcWSPresenceBeforePublishMsgEvent` | [TsgcWSPresenceBeforePublishMsgEvent](../types/TsgcWSPresenceBeforePublishMsgEvent.md) | `__property TsgcWSPresenceBeforePublishMsgEvent OnBeforePublishMsg;` |
| `OnBeforeSendMembers: TsgcWSPresenceBeforeSendMembersEvent` | [TsgcWSPresenceBeforeSendMembersEvent](../types/TsgcWSPresenceBeforeSendMembersEvent.md) | `__property TsgcWSPresenceBeforeSendMembersEvent OnBeforeSendMembers;` |
| `OnErrorMemberChannel: TsgcWSPresenceMemberChannelErrorEvent` | [TsgcWSPresenceMemberChannelErrorEvent](../types/TsgcWSPresenceMemberChannelErrorEvent.md) | `__property TsgcWSPresenceMemberChannelErrorEvent OnErrorMemberChannel;` |
| `OnErrorPublishMsg: TsgcWSPresencePublishMsgErrorEvent` | [TsgcWSPresencePublishMsgErrorEvent](../types/TsgcWSPresencePublishMsgErrorEvent.md) | `__property TsgcWSPresencePublishMsgErrorEvent OnErrorPublishMsg;` |

## Methods

Delphi

```pascal
procedure Broadcast(const aText: string; const aChannel: string = '');
```

C++Builder

```cpp
void __fastcall Broadcast(const UnicodeString aText, const UnicodeString aChannel = '');
```

