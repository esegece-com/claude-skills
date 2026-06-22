# TsgcWSPClient_Lightstreamer

unit: sgcWebSocket_Protocols
Edition: Standard

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AdapterSet: string` | `string` | `__property UnicodeString AdapterSet;` |
| `User: string` | `string` | `__property UnicodeString User;` |
| `Password: string` | `string` | `__property UnicodeString Password;` |
| `ClientId: string` | `string` | `__property UnicodeString ClientId;` |
| `HeartBeat: TsgcAI_MCP_Client_HeartBeatOptions` | [TsgcAI_MCP_Client_HeartBeatOptions](../types/TsgcAI_MCP_Client_HeartBeatOptions.md) | `__property TsgcAI_MCP_Client_HeartBeatOptions * HeartBeat;` |
| `LightstreamerOptions: TsgcLightstreamerOptions` | [TsgcLightstreamerOptions](../types/TsgcLightstreamerOptions.md) | `__property TsgcLightstreamerOptions * LightstreamerOptions;` |
| `Client: TsgcHTTP_API_Pinecone` | [TsgcHTTP_API_Pinecone](../types/TsgcHTTP_API_Pinecone.md) | `__property TsgcHTTP_API_Pinecone * Client;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnLightstreamerConnect: TsgcLightstreamerConnectEvent` | [TsgcLightstreamerConnectEvent](../types/TsgcLightstreamerConnectEvent.md) | `__property TsgcLightstreamerConnectEvent OnLightstreamerConnect;` |
| `OnLightstreamerDisconnect: TsgcLightstreamerDisconnectEvent` | [TsgcLightstreamerDisconnectEvent](../types/TsgcLightstreamerDisconnectEvent.md) | `__property TsgcLightstreamerDisconnectEvent OnLightstreamerDisconnect;` |
| `OnLightstreamerException: TsgcLightstreamerExceptionEvent` | [TsgcLightstreamerExceptionEvent](../types/TsgcLightstreamerExceptionEvent.md) | `__property TsgcLightstreamerExceptionEvent OnLightstreamerException;` |
| `OnLightstreamerSubscribe: TsgcLightstreamerSubscribeEvent` | [TsgcLightstreamerSubscribeEvent](../types/TsgcLightstreamerSubscribeEvent.md) | `__property TsgcLightstreamerSubscribeEvent OnLightstreamerSubscribe;` |
| `OnLightstreamerUnsubscribe: TsgcLightstreamerUnsubscribeEvent` | [TsgcLightstreamerUnsubscribeEvent](../types/TsgcLightstreamerUnsubscribeEvent.md) | `__property TsgcLightstreamerUnsubscribeEvent OnLightstreamerUnsubscribe;` |
| `OnLightstreamerUpdate: TsgcLightstreamerUpdateEvent` | [TsgcLightstreamerUpdateEvent](../types/TsgcLightstreamerUpdateEvent.md) | `__property TsgcLightstreamerUpdateEvent OnLightstreamerUpdate;` |
| `OnLightstreamerSnapshot: TsgcLightstreamerUpdateEvent` | [TsgcLightstreamerUpdateEvent](../types/TsgcLightstreamerUpdateEvent.md) | `__property TsgcLightstreamerUpdateEvent OnLightstreamerSnapshot;` |
| `OnLightstreamerEndOfSnapshot: TsgcLightstreamerItemEvent` | [TsgcLightstreamerItemEvent](../types/TsgcLightstreamerItemEvent.md) | `__property TsgcLightstreamerItemEvent OnLightstreamerEndOfSnapshot;` |
| `OnLightstreamerClearSnapshot: TsgcLightstreamerItemEvent` | [TsgcLightstreamerItemEvent](../types/TsgcLightstreamerItemEvent.md) | `__property TsgcLightstreamerItemEvent OnLightstreamerClearSnapshot;` |
| `OnLightstreamerOverflow: TsgcLightstreamerOverflowEvent` | [TsgcLightstreamerOverflowEvent](../types/TsgcLightstreamerOverflowEvent.md) | `__property TsgcLightstreamerOverflowEvent OnLightstreamerOverflow;` |
| `OnLightstreamerMessage: TsgcLightstreamerMessageEvent` | [TsgcLightstreamerMessageEvent](../types/TsgcLightstreamerMessageEvent.md) | `__property TsgcLightstreamerMessageEvent OnLightstreamerMessage;` |

