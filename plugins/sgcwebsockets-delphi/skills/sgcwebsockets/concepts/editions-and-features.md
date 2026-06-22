# Editions and Features

Components grouped by the minimum sgcWebSockets edition that includes them. Each edition is a superset of the ones above it: Standard < Professional < Enterprise < All-Access. A component listed under an edition is available in that edition and every higher one (All-Access components are the exception: they ship only in All-Access). Editions are derived from the library's `sgcVer.inc`.

## Indy dependency

sgcWebSockets is built on Indy, and which Indy it uses depends on the edition:

- **Standard** and **Professional** editions use the **standard Indy version that ships with Delphi**. Indy is included with Delphi and must be available in your IDE as usual.
- **Enterprise** and **All-Access** editions include and use **eSeGeCe's own custom Indy version**, bundled with the library and selected by the `SGC_CUSTOM_INDY` define. No separate Indy installation is needed for these editions.

This matters when resolving the `Id*` / `sgcId*` units in your `uses` clause and when troubleshooting Indy-related build issues: confirm which Indy your edition links against before changing Indy settings.

## Standard

Available in Standard and higher.

| Component | unit |
| --- | --- |
| [TsgcWSAPI_Discord](../reference/api/TsgcWSAPI_Discord.md) | sgcWebSocket_APIs |
| [TsgcLib_RCON](../reference/api/TsgcLib_RCON.md) | sgcLibs |
| [TsgcTDLib_Telegram](../reference/api/TsgcTDLib_Telegram.md) | sgcLibs |
| [TsgcHTTPAWS_SQS_Client](../reference/api/TsgcHTTPAWS_SQS_Client.md) | sgcHTTP |
| [TsgcHTTPGoogleCloud_PubSub_Client](../reference/api/TsgcHTTPGoogleCloud_PubSub_Client.md) | sgcHTTP |
| [TsgcHTTPGoogleCloud_Calendar_Client](../reference/api/TsgcHTTPGoogleCloud_Calendar_Client.md) | sgcHTTP |
| [TsgcHTTPGoogleCloud_FCM_Client](../reference/api/TsgcHTTPGoogleCloud_FCM_Client.md) | sgcHTTP |
| [TsgcHTTP_OAuth2_Client](../reference/api/TsgcHTTP_OAuth2_Client.md) | sgcHTTP |
| [TsgcHTTP_JWT_Client](../reference/api/TsgcHTTP_JWT_Client.md) | sgcHTTP |
| [TsgcWebView2](../reference/api/TsgcWebView2.md) | sgcWebView2 |
| [TsgcWSAPI_Bitfinex](../reference/api/TsgcWSAPI_Bitfinex.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Binance](../reference/api/TsgcWSAPI_Binance.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Binance_Futures](../reference/api/TsgcWSAPI_Binance_Futures.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Bitstamp](../reference/api/TsgcWSAPI_Bitstamp.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Huobi](../reference/api/TsgcWSAPI_Huobi.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Cex](../reference/api/TsgcWSAPI_Cex.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_CexPlus](../reference/api/TsgcWSAPI_CexPlus.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Bitmex](../reference/api/TsgcWSAPI_Bitmex.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Kraken](../reference/api/TsgcWSAPI_Kraken.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Kraken_Futures](../reference/api/TsgcWSAPI_Kraken_Futures.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Coinbase](../reference/api/TsgcWSAPI_Coinbase.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_ThreeCommas](../reference/api/TsgcWSAPI_ThreeCommas.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Kucoin](../reference/api/TsgcWSAPI_Kucoin.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Kucoin_Futures](../reference/api/TsgcWSAPI_Kucoin_Futures.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_OKX](../reference/api/TsgcWSAPI_OKX.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_XTB](../reference/api/TsgcWSAPI_XTB.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Bybit](../reference/api/TsgcWSAPI_Bybit.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_MEXC](../reference/api/TsgcWSAPI_MEXC.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_MEXC_Futures](../reference/api/TsgcWSAPI_MEXC_Futures.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Bitget](../reference/api/TsgcWSAPI_Bitget.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_GateIO](../reference/api/TsgcWSAPI_GateIO.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Deribit](../reference/api/TsgcWSAPI_Deribit.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_CryptoCom](../reference/api/TsgcWSAPI_CryptoCom.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_HTX](../reference/api/TsgcWSAPI_HTX.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_Forex](../reference/api/TsgcWSAPI_Forex.md) | sgcWebSocket_APIs |
| [TsgcIoTAmazon_MQTT_Client](../reference/api/TsgcIoTAmazon_MQTT_Client.md) | sgcIoT |
| [TsgcIoTAzure_MQTT_Client](../reference/api/TsgcIoTAzure_MQTT_Client.md) | sgcIoT |
| [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_WAMP2](../reference/api/TsgcWSPClient_WAMP2.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_STOMP](../reference/api/TsgcWSPClient_STOMP.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_STOMP_RabbitMQ](../reference/api/TsgcWSPClient_STOMP_RabbitMQ.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_STOMP_ActiveMQ](../reference/api/TsgcWSPClient_STOMP_ActiveMQ.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_AMQP](../reference/api/TsgcWSPClient_AMQP.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_AMQP1](../reference/api/TsgcWSPClient_AMQP1.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_Kafka](../reference/api/TsgcWSPClient_Kafka.md) | sgcWebSocket_Protocols |
| [TsgcTCPClient](../reference/api/TsgcTCPClient.md) | sgcTCP_Client_WS |
| [TsgcUDPCLient](../reference/api/TsgcUDPCLient.md) | sgcP2P |
| [TsgcSTUNClient](../reference/api/TsgcSTUNClient.md) | sgcP2P |
| [TsgcWSAPI_Pusher](../reference/api/TsgcWSAPI_Pusher.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_SignalR](../reference/api/TsgcWSAPI_SignalR.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_SignalRCore](../reference/api/TsgcWSAPI_SignalRCore.md) | sgcWebSocket_APIs |
| [TsgcWSAPI_SocketIO](../reference/api/TsgcWSAPI_SocketIO.md) | sgcWebSocket_APIs |
| [TsgcWSPClient_Lightstreamer](../reference/api/TsgcWSPClient_Lightstreamer.md) | sgcWebSocket_Protocols |
| [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md) | sgcWebSocket |
| [TsgcWebSocketClient_WinHTTP](../reference/api/TsgcWebSocketClient_WinHTTP.md) | sgcWebSocket |

## Professional

Available in Professional and higher.

| Component | unit |
| --- | --- |
| [TsgcWhatsApp_Client](../reference/api/TsgcWhatsApp_Client.md) | sgcLibs |
| [TsgcHTTP_Cryptohopper](../reference/api/TsgcHTTP_Cryptohopper.md) | sgcLibs |
| [TsgcWSPServer_WAMP](../reference/api/TsgcWSPServer_WAMP.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_WAMP](../reference/api/TsgcWSPClient_WAMP.md) | sgcWebSocket_Protocols |
| [TsgcUDPServer](../reference/api/TsgcUDPServer.md) | sgcP2P |
| [TsgcSTUNServer](../reference/api/TsgcSTUNServer.md) | sgcP2P |
| [TsgcWSPServer_WebRTC](../reference/api/TsgcWSPServer_WebRTC.md) | sgcWebSocket_Protocols |
| [TsgcWSPServer_AppRTC](../reference/api/TsgcWSPServer_AppRTC.md) | sgcWebSocket_Protocols |
| [TsgcWSAPIServer_RTCMultiConnection](../reference/api/TsgcWSAPIServer_RTCMultiConnection.md) | sgcWebSocket_Server_APIs |
| [TsgcWSPServer_broker](../reference/api/TsgcWSPServer_broker.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_broker](../reference/api/TsgcWSPClient_broker.md) | sgcWebSocket_Protocols |
| [TsgcWSPServer_sgc](../reference/api/TsgcWSPServer_sgc.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_sgc](../reference/api/TsgcWSPClient_sgc.md) | sgcWebSocket_Protocols |
| [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md) | sgcWebSocket_Protocols |
| [TsgcWSPServer_Files](../reference/api/TsgcWSPServer_Files.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_Files](../reference/api/TsgcWSPClient_Files.md) | sgcWebSocket_Protocols |
| [TsgcWSPServer_Presence](../reference/api/TsgcWSPServer_Presence.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_Presence](../reference/api/TsgcWSPClient_Presence.md) | sgcWebSocket_Protocols |
| [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md) | sgcWebSocket |
| [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md) | sgcWebSocket |
| [TsgcWebSocketProxyServer](../reference/api/TsgcWebSocketProxyServer.md) | sgcWebSocket |
| [TsgcWebSocketLoadBalancerServer](../reference/api/TsgcWebSocketLoadBalancerServer.md) | sgcWebSocket |
| [TsgcWebSocketFirewall](../reference/api/TsgcWebSocketFirewall.md) | sgcWebSocket |
| [TsgcWSRateLimiter](../reference/api/TsgcWSRateLimiter.md) | sgcWebSocket_Server_RateLimiter |
| [TsgcWSCircuitBreaker](../reference/api/TsgcWSCircuitBreaker.md) | sgcWebSocket_CircuitBreaker |
| [TsgcWSAPIKeyManager](../reference/api/TsgcWSAPIKeyManager.md) | sgcWebSocket_Server_APIKeyManager |

## Enterprise

Available in Enterprise and higher.

| Component | unit |
| --- | --- |
| [TsgcWSAPIServer_WebPush](../reference/api/TsgcWSAPIServer_WebPush.md) | sgcWebSocket_Server_APIs |
| [TsgcWebPush_Client](../reference/api/TsgcWebPush_Client.md) | sgcHTTP |
| [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md) | sgcHTTP |
| [TsgcHTTP_OAuth2_Server_Provider](../reference/api/TsgcHTTP_OAuth2_Server_Provider.md) | sgcHTTP |
| [TsgcHTTP_JWT_Server](../reference/api/TsgcHTTP_JWT_Server.md) | sgcHTTP |
| [TsgcWSAPIServer_WebAuthn](../reference/api/TsgcWSAPIServer_WebAuthn.md) | sgcWebSocket_Server_APIs |
| [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md) | sgcHTTP |
| [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md) | sgcHTTP |
| [TsgcWSAPIServer_OpenAPI](../reference/api/TsgcWSAPIServer_OpenAPI.md) | sgcWebSocket_Server_API_OpenAPI |
| [TsgcTURNClient](../reference/api/TsgcTURNClient.md) | sgcP2P |
| [TsgcTURNServer](../reference/api/TsgcTURNServer.md) | sgcP2P |
| [TsgcICEClient](../reference/api/TsgcICEClient.md) | sgcP2P |
| [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md) | sgcP2P |
| [TsgcWSPServer_RTCPeerConnection](../reference/api/TsgcWSPServer_RTCPeerConnection.md) | sgcWebSocket_Protocols |
| [TsgcAIChat](../reference/api/TsgcAIChat.md) | sgcAI |
| [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md) | sgcAI |
| [TsgcAIOpenAITranslator](../reference/api/TsgcAIOpenAITranslator.md) | sgcAI |
| [TsgcAIOpenAIAssistant](../reference/api/TsgcAIOpenAIAssistant.md) | sgcAI |
| [TsgcAudioRecorderMCI](../reference/api/TsgcAudioRecorderMCI.md) | sgcAI |
| [TsgcAudioPlayerMCI](../reference/api/TsgcAudioPlayerMCI.md) | sgcAI |
| [TsgcAudioRecorderWave](../reference/api/TsgcAudioRecorderWave.md) | sgcAI |
| [TsgcTextToSpeechSystem](../reference/api/TsgcTextToSpeechSystem.md) | sgcAI |
| [TsgcTextToSpeechGoogle](../reference/api/TsgcTextToSpeechGoogle.md) | sgcAI |
| [TsgcTextToSpeechAmazon](../reference/api/TsgcTextToSpeechAmazon.md) | sgcAI |
| [TsgcAIOpenAIEmbeddings](../reference/api/TsgcAIOpenAIEmbeddings.md) | sgcAI |
| [TsgcAIDatabaseVectorFile](../reference/api/TsgcAIDatabaseVectorFile.md) | sgcAI |
| [TsgcAIDatabaseVectorPinecone](../reference/api/TsgcAIDatabaseVectorPinecone.md) | sgcAI |
| [TsgcWSAPIServer_MCP](../reference/api/TsgcWSAPIServer_MCP.md) | sgcAI |
| [TsgcWSAPIClient_MCP](../reference/api/TsgcWSAPIClient_MCP.md) | sgcAI |
| [TsgcWSAPI_OpenAI](../reference/api/TsgcWSAPI_OpenAI.md) | sgcWebSocket_APIs |
| [TsgcWSPServer_E2EE](../reference/api/TsgcWSPServer_E2EE.md) | sgcWebSocket_Protocols |
| [TsgcWSPClient_E2EE](../reference/api/TsgcWSPClient_E2EE.md) | sgcWebSocket_Protocols |
| [TsgcWebSocketServer_HTTPAPI](../reference/api/TsgcWebSocketServer_HTTPAPI.md) | sgcWebSocket |

## All-Access

Available only in the All-Access edition.

| Component | unit |
| --- | --- |
| [TsgcHTMLPageBuilder](../reference/api/TsgcHTMLPageBuilder.md) | sgcHTML_Component |
| [TsgcHTMLThemeController](../reference/api/TsgcHTMLThemeController.md) | sgcHTML_Component |
| [TsgcHTMLEngine_Server](../reference/api/TsgcHTMLEngine_Server.md) | sgcHTML_Engine_Server |
| [TsgcHTMLComponent_Login](../reference/api/TsgcHTMLComponent_Login.md) | sgcHTML_Component_Login |
| [TsgcHTMLComponent_NavBar](../reference/api/TsgcHTMLComponent_NavBar.md) | sgcHTML_Component_NavBar |
| [TsgcHTMLComponent_Form](../reference/api/TsgcHTMLComponent_Form.md) | sgcHTML_Component_Form |
| [TsgcHTMLComponent_StatCard](../reference/api/TsgcHTMLComponent_StatCard.md) | sgcHTML_Component_StatCard |
| [TsgcHTMLComponent_Spinner](../reference/api/TsgcHTMLComponent_Spinner.md) | sgcHTML_Component_Spinner |
| [TsgcHTMLComponent_Sidebar](../reference/api/TsgcHTMLComponent_Sidebar.md) | sgcHTML_Component_Sidebar |
| [TsgcHTMLComponent_Modal](../reference/api/TsgcHTMLComponent_Modal.md) | sgcHTML_Component_Modal |
| [TsgcHTMLComponent_Toast](../reference/api/TsgcHTMLComponent_Toast.md) | sgcHTML_Component_Toast |
| [TsgcHTMLComponent_Pagination](../reference/api/TsgcHTMLComponent_Pagination.md) | sgcHTML_Component_Pagination |
| [TsgcHTMLComponent_Tabs](../reference/api/TsgcHTMLComponent_Tabs.md) | sgcHTML_Component_Tabs |
| [TsgcHTMLComponent_Breadcrumb](../reference/api/TsgcHTMLComponent_Breadcrumb.md) | sgcHTML_Component_Breadcrumb |
| [TsgcHTMLComponent_Accordion](../reference/api/TsgcHTMLComponent_Accordion.md) | sgcHTML_Component_Accordion |
| [TsgcHTMLComponent_Offcanvas](../reference/api/TsgcHTMLComponent_Offcanvas.md) | sgcHTML_Component_Offcanvas |
| [TsgcHTMLComponent_Chart](../reference/api/TsgcHTMLComponent_Chart.md) | sgcHTML_Component_Chart |
| [TsgcHTMLComponent_Gauge](../reference/api/TsgcHTMLComponent_Gauge.md) | sgcHTML_Component_Gauge |
| [TsgcHTMLComponent_Dropdown](../reference/api/TsgcHTMLComponent_Dropdown.md) | sgcHTML_Component_Dropdown |
| [TsgcHTMLComponent_Timeline](../reference/api/TsgcHTMLComponent_Timeline.md) | sgcHTML_Component_Timeline |
| [TsgcHTMLComponent_InputGroup](../reference/api/TsgcHTMLComponent_InputGroup.md) | sgcHTML_Component_InputGroup |
| [TsgcHTMLComponent_ButtonGroup](../reference/api/TsgcHTMLComponent_ButtonGroup.md) | sgcHTML_Component_ButtonGroup |
| [TsgcHTMLComponent_DataTable](../reference/api/TsgcHTMLComponent_DataTable.md) | sgcHTML_Component_DataTable |
| [TsgcHTMLComponent_Stepper](../reference/api/TsgcHTMLComponent_Stepper.md) | sgcHTML_Component_Stepper |
| [TsgcHTMLComponent_TreeView](../reference/api/TsgcHTMLComponent_TreeView.md) | sgcHTML_Component_TreeView |
| [TsgcHTMLComponent_Avatar](../reference/api/TsgcHTMLComponent_Avatar.md) | sgcHTML_Component_Avatar |
| [TsgcHTMLComponent_Rating](../reference/api/TsgcHTMLComponent_Rating.md) | sgcHTML_Component_Rating |
| [TsgcHTMLComponent_Calendar](../reference/api/TsgcHTMLComponent_Calendar.md) | sgcHTML_Component_Calendar |
| [TsgcHTMLComponent_FileUpload](../reference/api/TsgcHTMLComponent_FileUpload.md) | sgcHTML_Component_FileUpload |
| [TsgcHTMLDashboardLayout](../reference/api/TsgcHTMLDashboardLayout.md) | sgcHTML_Component_DashboardLayout |
| [TsgcHTMLComponent_Popover](../reference/api/TsgcHTMLComponent_Popover.md) | sgcHTML_Component_Popover |
| [TsgcHTMLComponent_Placeholder](../reference/api/TsgcHTMLComponent_Placeholder.md) | sgcHTML_Component_Placeholder |
| [TsgcHTMLComponent_Image](../reference/api/TsgcHTMLComponent_Image.md) | sgcHTML_Component_Image |
| [TsgcHTMLComponent_Video](../reference/api/TsgcHTMLComponent_Video.md) | sgcHTML_Component_Video |
| [TsgcHTMLComponent_Carousel](../reference/api/TsgcHTMLComponent_Carousel.md) | sgcHTML_Component_Carousel |
| [TsgcHTMLComponent_DatePicker](../reference/api/TsgcHTMLComponent_DatePicker.md) | sgcHTML_Component_DatePicker |
| [TsgcHTMLComponent_Select](../reference/api/TsgcHTMLComponent_Select.md) | sgcHTML_Component_Select |
| [TsgcHTMLComponent_Toolbar](../reference/api/TsgcHTMLComponent_Toolbar.md) | sgcHTML_Component_Toolbar |
| [TsgcHTMLComponent_Panel](../reference/api/TsgcHTMLComponent_Panel.md) | sgcHTML_Component_Panel |
| [TsgcHTMLComponent_ListGroup](../reference/api/TsgcHTMLComponent_ListGroup.md) | sgcHTML_Component_ListGroup |
| [TsgcHTMLComponent_SocialLogin](../reference/api/TsgcHTMLComponent_SocialLogin.md) | sgcHTML_Component_SocialLogin |
| [TsgcHTMLComponent_WebAuthnLogin](../reference/api/TsgcHTMLComponent_WebAuthnLogin.md) | sgcHTML_Component_WebAuthnLogin |
| [TsgcHTMLComponent_OAuthCallback](../reference/api/TsgcHTMLComponent_OAuthCallback.md) | sgcHTML_Component_OAuthCallback |
| [TsgcHTMLComponent_Grid](../reference/api/TsgcHTMLComponent_Grid.md) | sgcHTML_Component_Grid |
| [TsgcHTMLComponent_ChatBox](../reference/api/TsgcHTMLComponent_ChatBox.md) | sgcHTML_Component_ChatBox |
| [TsgcHTMLThemeBuilder](../reference/api/TsgcHTMLThemeBuilder.md) | sgcHTML_ThemeBuilder |
| [TsgcHTMLComponent_Notification](../reference/api/TsgcHTMLComponent_Notification.md) | sgcHTML_Component_Notification |
| [TsgcHTMLComponent_Map](../reference/api/TsgcHTMLComponent_Map.md) | sgcHTML_Component_Map |
| [TsgcHTMLComponent_KanbanBoard](../reference/api/TsgcHTMLComponent_KanbanBoard.md) | sgcHTML_Component_KanbanBoard |
| [TsgcHTMLComponent_Edit](../reference/api/TsgcHTMLComponent_Edit.md) | sgcHTML_Component_Edit |
| [TsgcHTMLComponent_Memo](../reference/api/TsgcHTMLComponent_Memo.md) | sgcHTML_Component_Edit |
| [TsgcHTMLComponent_CheckBox](../reference/api/TsgcHTMLComponent_CheckBox.md) | sgcHTML_Component_Edit |
| [TsgcHTMLComponent_RadioGroup](../reference/api/TsgcHTMLComponent_RadioGroup.md) | sgcHTML_Component_Edit |
| [TsgcHTMLComponent_RichEditor](../reference/api/TsgcHTMLComponent_RichEditor.md) | sgcHTML_Component_RichEditor |
| [TsgcHTMLComponent_AIChat](../reference/api/TsgcHTMLComponent_AIChat.md) | sgcHTML_Component_AIChat |
| [TsgcHTMLComponent_Chat](../reference/api/TsgcHTMLComponent_Chat.md) | sgcHTML_Component_Chat |
| [TsgcHTMLComponent_Scheduler](../reference/api/TsgcHTMLComponent_Scheduler.md) | sgcHTML_Component_Scheduler |
| [TsgcHTMLComponent_Gantt](../reference/api/TsgcHTMLComponent_Gantt.md) | sgcHTML_Component_Gantt |
| [TsgcHTMLComponent_Diagram](../reference/api/TsgcHTMLComponent_Diagram.md) | sgcHTML_Component_Diagram |
| [TsgcHTMLComponent_AutoComplete](../reference/api/TsgcHTMLComponent_AutoComplete.md) | sgcHTML_Component_AutoComplete |
| [TsgcHTMLComponent_Snackbar](../reference/api/TsgcHTMLComponent_Snackbar.md) | sgcHTML_Component_Snackbar |
| [TsgcHTMX_Engine_Server](../reference/api/TsgcHTMX_Engine_Server.md) | sgcHTMX_Engine_Server |
| [TsgcHTMX_Fragment](../reference/api/TsgcHTMX_Fragment.md) | sgcHTMX_Fragment |
| [TsgcHTMX_Router](../reference/api/TsgcHTMX_Router.md) | sgcHTMX_Router |

