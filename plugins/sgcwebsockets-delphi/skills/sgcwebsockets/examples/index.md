# Examples Catalog

Every shipped sgcWebSockets demo, grouped by category. Each entry lists the components it uses (linked to their API page) and the demo `dir` (under `delphi\Demos`).

Total demos: 120

## WebSocket Quick Start

### Server and Client Chat

A complete WebSocket chat application with server and client, featuring SSL/TLS, authentication, compression, and browser integration

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/01.Server_and_Client_Chat`

### WebSocket Clients APIs

Multi-protocol WebSocket client showcasing MQTT, STOMP, SignalR, SignalR Core, Socket.IO, Pusher, Discord, and AWS AppSync integrations

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md), [TsgcWSPClient_STOMP_RabbitMQ](../reference/api/TsgcWSPClient_STOMP_RabbitMQ.md), [TsgcWSAPI_SignalR](../reference/api/TsgcWSAPI_SignalR.md), [TsgcWSAPI_SignalRCore](../reference/api/TsgcWSAPI_SignalRCore.md), [TsgcWSAPI_SocketIO](../reference/api/TsgcWSAPI_SocketIO.md), [TsgcWSAPI_Pusher](../reference/api/TsgcWSAPI_Pusher.md), [TsgcWSAPI_Discord](../reference/api/TsgcWSAPI_Discord.md)

Demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs`

### Real Time Monitor

Server-side monitoring dashboard that pushes simulated CPU, memory, and network metrics to browser clients via the sgc pub/sub protocol

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md), [TsgcWSPServer_sgc](../reference/api/TsgcWSPServer_sgc.md)

Demo: `01.WebSocket_Quick_Start/03.Real_Time_Monitor`

### WebSocket Streams

Binary stream broadcasting demo where the server sends random bitmap images to all connected clients in real time

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/04.WebSocket_Streams`

### Upload File

WebSocket server that receives file uploads from browser clients using fragmented binary messages

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `01.WebSocket_Quick_Start/05.Upload_File`

### Authentication

WebSocket server demonstrating URL-based authentication with username/password validation

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `01.WebSocket_Quick_Start/06.Authentication`

### Firemonkey Server and Client

Cross-platform WebSocket chat using FireMonkey (FMX) framework, supporting Windows and Android deployment

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/07.Firemonkey_Server_and_Client`

### Client Test

WebSocket client for testing connections to various public and private WebSocket servers with TLS support

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/08.Client_Test`

### C++Builder Server and Client

Chat server and client written in C++Builder, demonstrating sgcWebSockets usage from C++ with SSL, authentication, compression, and HTTP/2

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/09.CBuilder_Server_and_Client`

### Library Application

Demonstrates packaging sgcWebSockets server and client into a shared DLL, consumed by separate server and client applications

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/10.Library_Application`

### Simple Game

Multiplayer game room system using WebSocket subscriptions for room-based messaging between two players

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/11.Simple_Game`

### Groups

Server-side group management with hierarchical group names and wildcard broadcasting to group members

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/12.Groups`

### Groups Users

Groups with user authentication, custom user data objects, and department-based group assignment

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `01.WebSocket_Quick_Start/14.Groups_Users`

## WebSocket Protocols

### SGC Generic PubSub Protocol

Client/Server demo showcasing the sgc proprietary protocol with publish/subscribe, RPC, notifications, QoS, and transactions

Components: [TsgcWSPClient_sgc](../reference/api/TsgcWSPClient_sgc.md), [TsgcWSPServer_sgc](../reference/api/TsgcWSPServer_sgc.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `02.WebSocket_Protocols/01.SGC_Generic_PubSub_Protocol`

### Send & Receive Files Protocol

Bidirectional file transfer between client and server with progress tracking, QoS, and broadcast support

Components: [TsgcWSPClient_Files](../reference/api/TsgcWSPClient_Files.md), [TsgcWSPServer_Files](../reference/api/TsgcWSPServer_Files.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `02.WebSocket_Protocols/02.Send_Receive_Files_Protocol`

### Presence Protocol

Real-time member presence tracking with channels, invitations, and publish/subscribe messaging

Components: [TsgcWSPClient_Presence](../reference/api/TsgcWSPClient_Presence.md), [TsgcWSPServer_Presence](../reference/api/TsgcWSPServer_Presence.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `02.WebSocket_Protocols/03.Presence_Protocol`

### WAMP Protocol

WebSocket Application Messaging Protocol with PubSub, RPC, progressive calls, and URI prefixes

Components: [TsgcWSPClient_WAMP](../reference/api/TsgcWSPClient_WAMP.md), [TsgcWSPServer_WAMP](../reference/api/TsgcWSPServer_WAMP.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `02.WebSocket_Protocols/04.WAMP_Protocol`

### DataSet Quotes Protocol

Real-time stock quotes synchronization between server and clients using the DataSet protocol

Components: [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md), [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `02.WebSocket_Protocols/05.DataSet_Quotes_Protocol`

### DataSet Tickets Protocol

Full ticketing CRUD application with bidirectional dataset synchronization, authentication, and browser support

Components: [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md), [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `02.WebSocket_Protocols/06.Dataset_Tickets_Protocol`

### SignalR Server and Client

Delphi SignalR client connecting to a C# SignalR server with hub messaging and group membership

Components: [TsgcWSAPI_SignalR](../reference/api/TsgcWSAPI_SignalR.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `02.WebSocket_Protocols/07.SignalR_Server_and_Client`

### MQTT Client

MQTT 3.1.1 client over WebSocket with subscribe, publish, QoS levels, retain, and ping support

Components: [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `02.WebSocket_Protocols/08.MQTT_Client`

### Binance Trade Futures

Binance COIN-M Futures trading demo with REST API orders and WebSocket ticker streaming

Components: [TsgcWSAPI_Binance_Futures](../reference/api/TsgcWSAPI_Binance_Futures.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `02.WebSocket_Protocols/09.Binance_Trade_Futures`

### AMQP 0.9.1 Client

Full-featured AMQP 0.9.1 client with channels, exchanges, queues, publishing, consuming, QoS, and transactions

Components: [TsgcWSPClient_AMQP](../reference/api/TsgcWSPClient_AMQP.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcTCPClient](../reference/api/TsgcTCPClient.md)

Demo: `02.WebSocket_Protocols/10.AMQP_Client`

### AMQP 1.0 Client

AMQP 1.0 client with sessions, sender/receiver links, Azure Service Bus CBS authentication, and message delivery states

Components: [TsgcWSPClient_AMQP1](../reference/api/TsgcWSPClient_AMQP1.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `02.WebSocket_Protocols/11.AMQP1_Client`

### E2EE (End-to-End Encryption)

Encrypted direct messaging and group chat with public key exchange, delivery acknowledgments, and user/group management

Components: [TsgcWSPClient_E2EE](../reference/api/TsgcWSPClient_E2EE.md), [TsgcWSPServer_E2EE](../reference/api/TsgcWSPServer_E2EE.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `02.WebSocket_Protocols/12.E2EE`

### Kafka Client

Apache Kafka protocol client with producer, consumer, admin, and offset management using the native Kafka wire protocol

Components: [TsgcWSPClient_Kafka](../reference/api/TsgcWSPClient_Kafka.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `02.WebSocket_Protocols/13.Kafka`

## WebSocket High Performance Server

### HTTP.SYS WebSocket Server

High-performance WebSocket chat server using the Windows HTTP Server API (http.sys) kernel-mode driver

Components: [TsgcWebSocketServer_HTTPAPI](../reference/api/TsgcWebSocketServer_HTTPAPI.md)

Demo: `03.WebSocket_High_Performance_Server/01.HTTP_SYS_WebSocket_Server`

### Indy IOCP Server

High-performance WebSocket server using Indy with Windows I/O Completion Ports (IOCP) for scalable asynchronous I/O

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `03.WebSocket_High_Performance_Server/02.Indy_IOCP_Server`

### Indy EPOLL Server

Console-based WebSocket echo server using Indy with EPOLL I/O handler for high-performance Linux deployments

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `03.WebSocket_High_Performance_Server/03.Indy_EPOLL_Server`

### WebSocket Benchmark Suite

Comprehensive benchmarking tool for measuring WebSocket server throughput, latency, and connection scalability across Indy and HTTPAPI backends

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), TsgcWSHTTPServer, TsgcWSServer_HTTPAPI

Demo: `03.WebSocket_High_Performance_Server/04.Benchmark`

## WebSocket Other Samples

### KendoUI Grid

Real-time editable data grid using Telerik KendoUI with WebSocket-powered CRUD operations and live push updates

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), TsgcJSON

Demo: `04.WebSocket_Other_Samples/01.KendoUI_Grid`

### SQLite Dataset Synchronization

Real-time dataset synchronization between server and client applications over WebSockets using FireDAC and SQLite

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md), [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md)

Demo: `04.WebSocket_Other_Samples/02.SQLLite`

### Load Balancer Server

WebSocket load balancer that distributes client connections across 3 backend servers with SSL/TLS, HTTP/2, and broadcast support

Components: [TsgcWebSocketLoadBalancerServer](../reference/api/TsgcWebSocketLoadBalancerServer.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `04.WebSocket_Other_Samples/03.LoadBalancer_Server`

### Server-Sent Events

WebSocket server with SSE fallback that broadcasts the current server time to all connected browser clients every 500ms

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `04.WebSocket_Other_Samples/04.ServerSentEvents`

### Proxy Server

WebSocket proxy server that bridges browser WebSocket connections to a backend TCP echo server

Components: [TsgcWebSocketProxyServer](../reference/api/TsgcWebSocketProxyServer.md), TIdECHOServer

Demo: `04.WebSocket_Other_Samples/05.Proxy_Server`

### FMX MQTT Client

Cross-platform FireMonkey MQTT client with subscribe, publish, and unsubscribe support using the MQTT 3.1.1 protocol

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md)

Demo: `04.WebSocket_Other_Samples/06.FMX_MQTT_Client`

### DevExtreme Grid

Real-time stock quotes grid using DevExtreme and the sgcWebSockets Dataset protocol with live data updates every 250ms

Components: [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md), [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md)

Demo: `04.WebSocket_Other_Samples/07.DevExtreme_Grid`

### Binance Console

Console application that streams real-time BNB/BTC ticker data from the Binance WebSocket API

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWSAPI_Binance](../reference/api/TsgcWSAPI_Binance.md)

Demo: `04.WebSocket_Other_Samples/08.Binance_Console`

### MQTT Console

Console-based MQTT client that connects to a RabbitMQ broker via WebSocket transport, subscribes to a topic, and prints received messages

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md)

Demo: `04.WebSocket_Other_Samples/09.MQTT_Console`

### Stream Video

HTTP video streaming server that serves MP4 files to browser clients with support for range requests and progressive playback

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `04.WebSocket_Other_Samples/10.StreamVideo`

### Users

User-to-user messaging system with named user registration and targeted message delivery over WebSockets

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), TsgcJSON, TsgcQueueCommon

Demo: `04.WebSocket_Other_Samples/11.Users`

### Forward HTTP

HTTP request forwarding (reverse proxy) that conditionally routes requests from a front-end server to a back-end server

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `04.WebSocket_Other_Samples/12.Forward_HTTP`

### Firewall Demo

Comprehensive WebSocket firewall with IP filtering, content inspection, GeoIP blocking, threat scoring, and custom rule engine

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketFirewall](../reference/api/TsgcWebSocketFirewall.md)

Demo: `04.WebSocket_Other_Samples/13.Firewall`

## Crypto

### Binance API Client

Connect to the Binance cryptocurrency exchange via WebSocket and REST APIs for spot trading, futures, and wallet operations

Components: [TsgcWSAPI_Binance](../reference/api/TsgcWSAPI_Binance.md), [TsgcWSAPI_Binance_Futures](../reference/api/TsgcWSAPI_Binance_Futures.md)

Demo: `05.Crypto/01.Binance`

### Bitstamp API Client

Connect to the Bitstamp cryptocurrency exchange via WebSocket (Pusher) and REST APIs for real-time market data and trading

Components: [TsgcWSAPI_Bitstamp](../reference/api/TsgcWSAPI_Bitstamp.md)

Demo: `05.Crypto/02.Bitstamp`

### Huobi API Client

Connect to the Huobi (HTX) cryptocurrency exchange via WebSocket for real-time market data subscriptions

Components: [TsgcWSAPI_Huobi](../reference/api/TsgcWSAPI_Huobi.md)

Demo: `05.Crypto/03.Huobi`

### CEX.IO API Client

Connect to the CEX.IO cryptocurrency exchange via WebSocket for real-time market data, authentication, and trading operations

Components: [TsgcWSAPI_Cex](../reference/api/TsgcWSAPI_Cex.md)

Demo: `05.Crypto/04.Cex`

### CEX.IO Plus API Client

Connect to the CEX.IO Plus (advanced) WebSocket API for real-time order books, trades, candles, and private account management

Components: [TsgcWSAPI_CexPlus](../reference/api/TsgcWSAPI_CexPlus.md)

Demo: `05.Crypto/05.CexPlus`

### BitMEX API Client

Connect to the BitMEX cryptocurrency derivatives exchange via WebSocket and REST APIs for futures trading, order management, and market data

Components: [TsgcWSAPI_Bitmex](../reference/api/TsgcWSAPI_Bitmex.md)

Demo: `05.Crypto/06.Bitmex`

### Kraken API Client

Connect to the Kraken cryptocurrency exchange via WebSocket and REST APIs for spot and futures trading, with comprehensive market data and account management

Components: [TsgcWSAPI_Kraken](../reference/api/TsgcWSAPI_Kraken.md), [TsgcWSAPI_Kraken_Futures](../reference/api/TsgcWSAPI_Kraken_Futures.md)

Demo: `05.Crypto/08.Kraken`

### Coinbase API Client

Connect to the Coinbase Advanced Trade API via WebSocket and REST for real-time market data, order management, and account operations

Components: [TsgcWSAPI_Coinbase](../reference/api/TsgcWSAPI_Coinbase.md)

Demo: `05.Crypto/09.Coinbase`

### 3Commas API Client

Connect to the 3Commas automated trading platform via WebSocket and REST APIs for bot management, smart trades, and multi-exchange account operations

Components: [TsgcWSAPI_ThreeCommas](../reference/api/TsgcWSAPI_ThreeCommas.md)

Demo: `05.Crypto/10.ThreeCommas`

### Kucoin API Demo

Demonstrates integration with the Kucoin cryptocurrency exchange via WebSocket and REST APIs, supporting both Spot and Futures markets.

Components: [TsgcWSAPI_Kucoin](../reference/api/TsgcWSAPI_Kucoin.md), [TsgcWSAPI_Kucoin_Futures](../reference/api/TsgcWSAPI_Kucoin_Futures.md)

Demo: `05.Crypto/11.Kucoin`

### OKX API Demo

Demonstrates integration with the OKX cryptocurrency exchange via WebSocket for public and private channels, plus order placement.

Components: [TsgcWSAPI_OKX](../reference/api/TsgcWSAPI_OKX.md)

Demo: `05.Crypto/12.OKX`

### XTB Broker API Demo

Demonstrates integration with the XTB online trading broker via WebSocket for trading data and streaming market subscriptions.

Components: [TsgcWSAPI_XTB](../reference/api/TsgcWSAPI_XTB.md)

Demo: `05.Crypto/13.XTB`

### Bybit API Demo

Demonstrates integration with the Bybit cryptocurrency derivatives exchange via WebSocket and REST APIs, supporting Spot, Linear, Inverse, and Option markets.

Components: [TsgcWSAPI_Bybit](../reference/api/TsgcWSAPI_Bybit.md)

Demo: `05.Crypto/14.Bybit`

### MEXC API Demo

Demonstrates integration with the MEXC cryptocurrency exchange via WebSocket and REST APIs, supporting both Spot and Futures markets.

Components: [TsgcWSAPI_MEXC](../reference/api/TsgcWSAPI_MEXC.md), [TsgcWSAPI_MEXC_Futures](../reference/api/TsgcWSAPI_MEXC_Futures.md)

Demo: `05.Crypto/15.MEXC`

### Bitget API Demo

Demonstrates integration with the Bitget cryptocurrency exchange via WebSocket and REST APIs for spot trading.

Components: [TsgcWSAPI_Bitget](../reference/api/TsgcWSAPI_Bitget.md)

Demo: `05.Crypto/16.Bitget`

### Gate.io API Demo

Demonstrates integration with the Gate.io cryptocurrency exchange via WebSocket and REST APIs for spot trading.

Components: [TsgcWSAPI_GateIO](../reference/api/TsgcWSAPI_GateIO.md)

Demo: `05.Crypto/17.GateIO`

### Deribit API Demo

Demonstrates integration with the Deribit cryptocurrency derivatives exchange via WebSocket and REST APIs, specializing in BTC/ETH futures and options.

Components: [TsgcWSAPI_Deribit](../reference/api/TsgcWSAPI_Deribit.md)

Demo: `05.Crypto/18.Deribit`

### Crypto.com API Demo

Demonstrates integration with the Crypto.com cryptocurrency exchange via WebSocket and REST APIs for market data and trading.

Components: [TsgcWSAPI_CryptoCom](../reference/api/TsgcWSAPI_CryptoCom.md)

Demo: `05.Crypto/19.CryptoCom`

### HTX (Huobi) API Demo

Demonstrates integration with the HTX (formerly Huobi) cryptocurrency exchange via WebSocket and REST APIs for market data subscriptions.

Components: [TsgcWSAPI_HTX](../reference/api/TsgcWSAPI_HTX.md), TsgcHTTP_API_HTX

Demo: `05.Crypto/20.HTX`

### Bitfinex API Demo

Demonstrates integration with the Bitfinex cryptocurrency exchange via WebSocket for real-time market data subscriptions and configuration.

Components: [TsgcWSAPI_Bitfinex](../reference/api/TsgcWSAPI_Bitfinex.md)

Demo: `05.Crypto/21.Bitfinex`

## IoT Clients

### Azure IoT Windows Service

A headless Windows Service that connects to Azure IoT Hub, subscribes to cloud-to-device messages, and logs all activity to a file

Components: [TsgcIoTAzure_MQTT_Client](../reference/api/TsgcIoTAzure_MQTT_Client.md)

Demo: `10.IoT_Clients/AzureWindowsService`

### IoT Client (Amazon AWS & Azure)

MQTT-based IoT client demonstrating connectivity to Amazon AWS IoT Core and Microsoft Azure IoT Hub with multiple authentication methods

Components: [TsgcIoTAmazon_MQTT_Client](../reference/api/TsgcIoTAmazon_MQTT_Client.md), [TsgcIoTAzure_MQTT_Client](../reference/api/TsgcIoTAzure_MQTT_Client.md)

Demo: `10.IoT_Clients`

## AI

### OpenAI RealTime API

Live audio transcription using the OpenAI RealTime WebSocket API with microphone input and streaming results

Components: [TsgcWSAPI_OpenAI](../reference/api/TsgcWSAPI_OpenAI.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcAudioRecorderWave](../reference/api/TsgcAudioRecorderWave.md)

Demo: `15.AI/01.QuickStart/06.RealTime`

### AI ChatBot

Voice-driven AI chatbot using OpenAI speech-to-text and text-to-speech with multi-language support

Components: [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md)

Demo: `15.AI/02.Applications/01.ChatBot`

### AI Translator

Real-time voice translation using OpenAI Whisper transcription with optional text-to-speech output

Components: [TsgcAIOpenAITranslator](../reference/api/TsgcAIOpenAITranslator.md)

Demo: `15.AI/02.Applications/02.Translator`

### Questions & Answers

Retrieval-Augmented Generation (RAG) using OpenAI embeddings with file-based or Pinecone vector databases

Components: [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md), [TsgcAIOpenAIEmbeddings](../reference/api/TsgcAIOpenAIEmbeddings.md)

Demo: `15.AI/02.Applications/03.QA`

### Code Converter

AI-powered source code translation between Delphi, C++Builder, .NET, and Python using ChatGPT

Components: [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md)

Demo: `15.AI/02.Applications/04.CodeConverter`

### OpenAI Assistant

Full-featured OpenAI Assistants API client with Code Interpreter, File Search, Function Calling, and Streaming

Components: [TsgcAIOpenAIAssistant](../reference/api/TsgcAIOpenAIAssistant.md)

Demo: `15.AI/02.Applications/05.Assistant`

### MCP Server

Model Context Protocol server exposing Tools, Prompts, and Resources over HTTP/SSE with authentication support

Components: [TsgcWSAPIServer_MCP](../reference/api/TsgcWSAPIServer_MCP.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `15.AI/03.MCP/01.MCP_Server`

### MCP Client

Model Context Protocol client for discovering and invoking Tools, Prompts, and Resources from MCP servers

Components: [TsgcWSAPIClient_MCP](../reference/api/TsgcWSAPIClient_MCP.md)

Demo: `15.AI/03.MCP/02.MCP_Client`

## HTTP Protocol

### HTTP/2 Server and Client

A complete HTTP/2 server and client demonstrating request/response, performance comparison with HTTP/1.1, latency testing, and httpbin.org API integration.

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `20.HTTP_Protocol/01.HTTP2_Server_And_Client`

### OAuth2 Authentication

OAuth2 client and server demonstrating authorization code flow, PKCE, client credentials, token refresh, and DPoP (RFC 9449) with multiple provider presets.

Components: [TsgcHTTP_OAuth2_Client](../reference/api/TsgcHTTP_OAuth2_Client.md), [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/02.OAuth2_Authentication`

### Google Pub/Sub

Google Cloud Pub/Sub API client with OAuth2 and Service Account (JWT) authentication, supporting topic and subscription management, message publishing, and pull delivery.

Components: [TsgcHTTPGoogleCloud_PubSub_Client](../reference/api/TsgcHTTPGoogleCloud_PubSub_Client.md)

Demo: `20.HTTP_Protocol/03.Google/01.Google_PubSub`

### Google Calendar

Full-featured Google Calendar API client with calendar and event management, ACL control, freebusy queries, sync tokens, and both OAuth2 and Service Account authentication.

Components: [TsgcHTTPGoogleCloud_Calendar_Client](../reference/api/TsgcHTTPGoogleCloud_Calendar_Client.md)

Demo: `20.HTTP_Protocol/03.Google/02.Google_Calendar`

### Google FCM

Google Firebase Cloud Messaging (FCM) client for sending push notifications via the FCM HTTP v1 API with OAuth2 or Service Account authentication.

Components: [TsgcHTTPGoogleCloud_FCM_Client](../reference/api/TsgcHTTPGoogleCloud_FCM_Client.md)

Demo: `20.HTTP_Protocol/03.Google/03.Google_FCM`

### Amazon SQS

Amazon Simple Queue Service (SQS) client demonstrating queue management, message sending/receiving, and attribute configuration using AWS Signature V4 authentication.

Components: [TsgcHTTPAWS_SQS_Client](../reference/api/TsgcHTTPAWS_SQS_Client.md)

Demo: `20.HTTP_Protocol/04.AWS/01.Amazon_SQS`

### JWT Authentication

JSON Web Token (JWT) server and client demonstrating token-based WebSocket authentication with configurable algorithms, issuer, expiration, and validity windows.

Components: [TsgcHTTP_JWT_Server](../reference/api/TsgcHTTP_JWT_Server.md), [TsgcHTTP_JWT_Client](../reference/api/TsgcHTTP_JWT_Client.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `20.HTTP_Protocol/05.JWT`

### HTTP Post Big File

HTTP server demonstrating large file upload via browser POST, using file-stream persistence to handle big uploads without exhausting memory.

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/06.HTTP_Post_Big_File`

### Apple Push Notifications

Send Apple Push Notifications (APNs) via HTTP/2 using either certificate-based or token-based (JWT ES256) authentication with SChannel TLS.

Components: [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md), [TsgcHTTP_JWT_Client](../reference/api/TsgcHTTP_JWT_Client.md)

Demo: `20.HTTP_Protocol/07.Apple_Push_Notifications`

### OAuth2 Server Provider

HTTP server acting as an OAuth2 resource server, integrating Azure AD as the identity provider to protect private endpoints with token-based access control.

Components: [TsgcHTTP_OAuth2_Server_Provider](../reference/api/TsgcHTTP_OAuth2_Server_Provider.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/08.OAuth2_ServerProvider`

### WebPush Notifications

Web Push notification server using VAPID authentication, supporting browser subscription management and broadcast notifications to Chrome, Edge, Firefox, and Safari.

Components: [TsgcWSAPIServer_WebPush](../reference/api/TsgcWSAPIServer_WebPush.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/11.WebPush_Notifications`

### WebAuthn

WebAuthn/FIDO2 passwordless authentication server with passkey registration, authentication, and FIDO Metadata Service (MDS) integration.

Components: [TsgcWSAPIServer_WebAuthn](../reference/api/TsgcWSAPIServer_WebAuthn.md), [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/12.WebAuthn`

### HTTP/2 Large File Transfer

HTTP/2 server and client for transferring large files (1+ GB) with both synchronous and asynchronous download modes, progress tracking, and speed measurement.

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `20.HTTP_Protocol/13.HTTP2_LargeFile_Transfer`

### Benchmark HTTP/2 vs HTTP/3

Performance benchmarking tool comparing HTTP/2 (TCP+TLS) and HTTP/3 (QUIC) with configurable iterations, high-resolution timing, and detailed statistical output.

Components: [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md), TsgcHTTP3Client

Demo: `20.HTTP_Protocol/14.Benchmark_HTTP2_vs_HTTP3`

### OpenAPI Server (Spec-First)

OpenAPI 3.0 server loading a Petstore specification file, with automatic routing, request validation, Swagger UI, and CORS support.

Components: TsgcWSServer_API_OpenAPI, [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/15.OpenAPI_Server_SpecFirst`

### OpenAPI Server (Code-First)

Code-first OpenAPI server using Delphi RTTI attributes to define API contracts, automatically generating the OpenAPI 3.0 spec from annotated service classes.

Components: TsgcWSServer_API_OpenAPI, TsgcOpenAPICodeFirstScanner, [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)

Demo: `20.HTTP_Protocol/16.OpenAPI_Server_CodeFirst`

## GRPC

### gRPC Client

Comprehensive gRPC client demonstrating all four RPC patterns, interceptors, retry policies, load balancing, health checks, reflection, and telemetry

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/01.GRPC_Client`

### Google Cloud Pub/Sub gRPC

Publish and subscribe to messages on Google Cloud Pub/Sub using the native gRPC API with protobuf serialization

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTPGoogleCloud_PubSub_Client](../reference/api/TsgcHTTPGoogleCloud_PubSub_Client.md)

Demo: `21.GRPC/10.PubSub`

### Google Cloud Speech-to-Text gRPC

Transcribe audio files stored in Google Cloud Storage using the Speech-to-Text v1 gRPC API

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/11.Speech_to_Text`

### Google Cloud Translation gRPC

Translate text, detect languages, and list supported languages using the Cloud Translation v3 gRPC API

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/12.Translation`

### Google Cloud Vision gRPC

Analyze images with the Cloud Vision API to detect labels, landmarks, logos, text, faces, and more via gRPC

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/13.Vision`

### Google Cloud Natural Language gRPC

Analyze text for sentiment, entities, and content classification using the Natural Language v1 gRPC API

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/14.Natural_Language`

### Google Cloud Storage gRPC

Manage buckets and objects in Google Cloud Storage using the Storage v2 gRPC API

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/15.Cloud_Storage`

### Google Cloud BigQuery Storage gRPC

Read large datasets from BigQuery tables using the high-throughput BigQuery Storage Read API via gRPC streaming

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/16.BigQuery`

### Google Vertex AI gRPC

Generate content using Google Gemini models through the Vertex AI PredictionService gRPC API

Components: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md), [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)

Demo: `21.GRPC/17.Vertex_AI`

## Mobile

### Mobile WebSocket Client

A cross-platform FireMonkey WebSocket chat client for mobile devices (Android, iOS) and desktop

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)

Demo: `25.Mobile/01.Mobile Client`

### Android Notification Service

An Android background service that maintains a WebSocket connection and delivers incoming messages as local notifications

Components: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), TNotificationCenter

Demo: `25.Mobile/02.Android_Service`

## WebRTC Protocol

### AppRTC Video Chat Server

WebSocket-based signaling server implementing the AppRTC protocol for browser-to-browser video chat

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWSPServer_AppRTC](../reference/api/TsgcWSPServer_AppRTC.md)

Demo: `30.WebRTC_Protocol/01.AppRTC`

### WebRTC Video Server

WebSocket signaling server with the WebRTC protocol for channel-based peer-to-peer video communication

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWSPServer_WebRTC](../reference/api/TsgcWSPServer_WebRTC.md)

Demo: `30.WebRTC_Protocol/03.WebRTC`

### RTCMultiConnection Server

Multi-party WebRTC server supporting video conferencing, screen sharing, video broadcasting, and audio conferencing via Socket.IO signaling

Components: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md), [TsgcWSAPIServer_RTCMultiConnection](../reference/api/TsgcWSAPIServer_RTCMultiConnection.md)

Demo: `30.WebRTC_Protocol/04.RTCMultiConnection`

## P2P

### UDP Server & Client

Basic UDP communication with optional DTLS encryption, demonstrating the foundation for P2P networking

Components: [TsgcUDPServer](../reference/api/TsgcUDPServer.md), [TsgcUDPClient](../reference/api/TsgcUDPClient.md)

Demo: `35.P2P/01.UDP_Server_Client`

### STUN Server & Client

Session Traversal Utilities for NAT (RFC 5389) - discover public IP addresses and NAT types for P2P connectivity

Components: [TsgcSTUNServer](../reference/api/TsgcSTUNServer.md), [TsgcSTUNClient](../reference/api/TsgcSTUNClient.md)

Demo: `35.P2P/02.STUN`

### TURN Server & Client

Traversal Using Relays around NAT (RFC 5766) - relay server for P2P connectivity when direct connections fail

Components: [TsgcTURNServer](../reference/api/TsgcTURNServer.md), [TsgcTURNClient](../reference/api/TsgcTURNClient.md)

Demo: `35.P2P/03.TURN`

### ICE Client & Signaling Server

Interactive Connectivity Establishment (RFC 8445) - gather, exchange, and test ICE candidates to find the best P2P connection path

Components: [TsgcICEClient](../reference/api/TsgcICEClient.md), [TsgcTURNClient](../reference/api/TsgcTURNClient.md), [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md), [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `35.P2P/04.ICE`

### RTCPeerConnection

High-level P2P connection component with integrated WebSocket signaling, ICE negotiation, optional DTLS, and text messaging

Components: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md), [TsgcWSPServer_RTCPeerConnection](../reference/api/TsgcWSPServer_RTCPeerConnection.md), [TsgcWebSocketServer](../reference/api/TsgcWebSocketServer.md)

Demo: `35.P2P/05.RTCPeerConnection`

### WebRTC DataChannel

Bidirectional data channels over SCTP for sending text and binary data through peer-to-peer connections

Components: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md), TsgcSCTP_Association, TsgcRTCDataChannel_Manager, TsgcRTCDataChannel

Demo: `35.P2P/06.DataChannel`

### WebRTC Audio Call

Peer-to-peer voice calling with Opus codec, microphone capture, speaker playback, and real-time audio level monitoring

Components: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md), TsgcRTC_AudioSession, TsgcAudioCapture_Win, TsgcAudioRenderer_Win

Demo: `35.P2P/07.AudioCall`

### WebRTC Video Call

Full peer-to-peer video and audio calling with Opus audio, VP8 video, local/remote video preview, and real-time audio level monitoring

Components: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md), TsgcRTC_AudioSession, TsgcRTC_VideoSession, TsgcAudioCapture_Win, TsgcAudioRenderer_Win, TsgcVideoCapture_Win, TsgcVideoRenderer_Win

Demo: `35.P2P/08.VideoCall`

## DataSnap

### DataSnap Server (HTTP API)

A DataSnap WebBroker Bridge server using the Windows HTTP API (http.sys) with integrated WebSocket and OAuth2 support

Components: TsgcWSServer_HTTPAPI_WebBrokerBridge, [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md)

Demo: `40.DataSnap/Server_HTTPAPI`

### DataSnap Server (Indy HTTP)

A DataSnap WebBroker Bridge server using Indy HTTP with configurable SSL/TLS, OpenSSL versions, and OAuth2 authentication

Components: TsgcWSHTTPWebBrokerBridgeServer, [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md)

Demo: `40.DataSnap/Server_Indy_HTTP`

### DataSnap Server (Indy HTTP/2)

A DataSnap WebBroker Bridge server using HTTP/2 with SSL/TLS, WebSocket echo, OAuth2, and a companion DataSnap TCP client

Components: TsgcWSHTTP2WebBrokerBridgeServer, [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md)

Demo: `40.DataSnap/Server_Indy_HTTP2`

## Other

### Telegram Client

A full-featured Telegram desktop client using TDLib, supporting user and bot login, chat management, messaging, file sharing, and proxy configuration

Components: [TsgcTDLib_Telegram](../reference/api/TsgcTDLib_Telegram.md)

Demo: `50.Other/01.Telegram_Client`

### RCON Client

Remote Console (RCON) client for sending commands to game servers like Minecraft, Rust, and other Source Engine games

Components: [TsgcLib_RCON](../reference/api/TsgcLib_RCON.md)

Demo: `50.Other/02.RCON`

### Cryptohopper Client

Full API client for the Cryptohopper automated crypto trading platform with OAuth2 authentication, trading, webhooks, and signals

Components: [TsgcHTTP_Cryptohopper](../reference/api/TsgcHTTP_Cryptohopper.md)

Demo: `50.Other/03.Cryptohopper`

### WhatsApp Cloud API Client

A WhatsApp Business Cloud API client and webhook server for sending/receiving messages including text, images, documents, contacts, locations, interactive lists, and buttons

Components: [TsgcWhatsApp_Client](../reference/api/TsgcWhatsApp_Client.md)

Demo: `50.Other/05.WhatsApp`

### WebView2 Browser

A full-featured web browser built with the sgcWebView2 component, demonstrating navigation, JavaScript execution, cookies, printing, downloads, virtual hosts, and comprehensive event logging

Components: [TsgcWebView2](../reference/api/TsgcWebView2.md)

Demo: `50.Other/06.WebView2_Browser`

### WebView2 Browser

A full-featured web browser built with the sgcWebView2 component, demonstrating navigation, JavaScript execution, cookies, printing, downloads, virtual hosts, and comprehensive event logging

Components: [TsgcWebView2](../reference/api/TsgcWebView2.md)

Demo: `50.Other/WebView2_Browser`

