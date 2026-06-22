# TsgcWSPClient_Presence

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Presence: TsgcWSPresenceMember_Options` | [TsgcWSPresenceMember_Options](../types/TsgcWSPresenceMember_Options.md) | `__property TsgcWSPresenceMember_Options * Presence;` |
| `Acknowledgment: TsgcWSAckClient_Options` | [TsgcWSAckClient_Options](../types/TsgcWSAckClient_Options.md) | `__property TsgcWSAckClient_Options * Acknowledgment;` |
| `EncodeBase64: Boolean` | `Boolean` | `__property bool EncodeBase64;` |
| `Client: TsgcHTTP_API_Pinecone` | [TsgcHTTP_API_Pinecone](../types/TsgcHTTP_API_Pinecone.md) | `__property TsgcHTTP_API_Pinecone * Client;` |
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
| `OnSession: TsgcWSPresenceSessionEvent` | [TsgcWSPresenceSessionEvent](../types/TsgcWSPresenceSessionEvent.md) | `__property TsgcWSPresenceSessionEvent OnSession;` |
| `OnNewMember: TsgcWSPresenceNewMemberEvent` | [TsgcWSPresenceNewMemberEvent](../types/TsgcWSPresenceNewMemberEvent.md) | `__property TsgcWSPresenceNewMemberEvent OnNewMember;` |
| `OnRemoveMember: TsgcWSPresenceRemoveMemberEvent` | [TsgcWSPresenceRemoveMemberEvent](../types/TsgcWSPresenceRemoveMemberEvent.md) | `__property TsgcWSPresenceRemoveMemberEvent OnRemoveMember;` |
| `OnNewChannelMember: TsgcWSPresenceNewMemberChannelEvent` | [TsgcWSPresenceNewMemberChannelEvent](../types/TsgcWSPresenceNewMemberChannelEvent.md) | `__property TsgcWSPresenceNewMemberChannelEvent OnNewChannelMember;` |
| `OnRemoveChannelMember: TsgcWSPresenceRemoveMemberChannelEvent` | [TsgcWSPresenceRemoveMemberChannelEvent](../types/TsgcWSPresenceRemoveMemberChannelEvent.md) | `__property TsgcWSPresenceRemoveMemberChannelEvent OnRemoveChannelMember;` |
| `OnPublishMsg: TsgcWSPresencePublishMsgEvent` | [TsgcWSPresencePublishMsgEvent](../types/TsgcWSPresencePublishMsgEvent.md) | `__property TsgcWSPresencePublishMsgEvent OnPublishMsg;` |
| `OnGetMembers: TsgcWSPresenceGetMembersEvent` | [TsgcWSPresenceGetMembersEvent](../types/TsgcWSPresenceGetMembersEvent.md) | `__property TsgcWSPresenceGetMembersEvent OnGetMembers;` |
| `OnErrorMemberChannel: TsgcWSPresenceMemberChannelErrorEvent` | [TsgcWSPresenceMemberChannelErrorEvent](../types/TsgcWSPresenceMemberChannelErrorEvent.md) | `__property TsgcWSPresenceMemberChannelErrorEvent OnErrorMemberChannel;` |
| `OnErrorPublishMsg: TsgcWSPresencePublishMsgErrorEvent` | [TsgcWSPresencePublishMsgErrorEvent](../types/TsgcWSPresencePublishMsgErrorEvent.md) | `__property TsgcWSPresencePublishMsgErrorEvent OnErrorPublishMsg;` |
| `OnChannelInvitation: TsgcWSPresenceChannelInvitationEvent` | [TsgcWSPresenceChannelInvitationEvent](../types/TsgcWSPresenceChannelInvitationEvent.md) | `__property TsgcWSPresenceChannelInvitationEvent OnChannelInvitation;` |
| `OnChannelInvitationResponse: TsgcWSPresenceChannelResultEvent` | [TsgcWSPresenceChannelResultEvent](../types/TsgcWSPresenceChannelResultEvent.md) | `__property TsgcWSPresenceChannelResultEvent OnChannelInvitationResponse;` |

## Methods

Delphi

```pascal
procedure WriteData(const aText: String);
procedure Subscribe(const aChannel: String);
procedure UnSubscribe(const aChannel: String);
procedure Invite(const aChannel, aMemberID: String);
procedure GetMembers;
procedure Publish(const aText: String; const aChannel: String = '');
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText);
void __fastcall Subscribe(const UnicodeString aChannel);
void __fastcall UnSubscribe(const UnicodeString aChannel);
void __fastcall Invite(const UnicodeString aChannel, const UnicodeString aMemberID);
void __fastcall GetMembers();
void __fastcall Publish(const UnicodeString aText, const UnicodeString aChannel = '');
```

