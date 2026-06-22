# Version history

Changes per sgcWebSockets release, newest first. Source: history.txt.

*******************************************************

 sgcWebSockets

*******************************************************

 [*] : Bug
 [+] : New
 [-] : Deleted
 [/] : Breaking changes

Versions
--------

## 2026.7.0: 2026 July

 [+] : New client option Options.WaitForConnect (default False). When enabled, the synchronous Connect() returns only after the OnConnect event has fired, so for sub-protocols that establish a session on connect (such as the sgc protocol) the connection is fully ready when Connect() returns. This prevents a connect-readiness race on fast reconnects, where code that uses the connection immediately after Connect() could run before the sub-protocol OnConnect had fired and close a healthy connection. Effective when NotifyEvents is neNoSync.

 [*] : Fixed a double-free in the WebSocket servers when the same connection was notified for disconnection more than once (for example an error path racing the normal close), which could stop the server under strict memory managers such as FastMM.





## 2026.6.0: 2026 June

 [+] : New OpenAPI Server component: server-side OpenAPI 3.x request router for TsgcWebSocketHTTPServer. Loads an OpenAPI spec, validates incoming HTTP requests (path/query/header/body) against the spec, dispatches to user-supplied operation handlers and returns RFC 7807 problem+json on validation errors.
 [+] : New Demos in the folder "Demos/23.OpenAPI" showing the main features of the OpenAPI Server.
 [+] : New TsgcGRPCClient component: gRPC client over HTTP/2 (TsgcHTTP2Client) supporting the four RPC patterns (unary, server streaming, client streaming and bidirectional streaming), with channel options (compression and content-type), default and per-call metadata, deadlines, automatic retries with exponential backoff, client-side load balancing (Pick First and Round Robin), gRPC Health Checking (Check and Watch), Server Reflection, interceptors (logging, timeout, metadata) and OpenTelemetry metrics.
 [+] : New gRPC interfaces for Google Cloud services, built on TsgcGRPCClient with typed protobuf request and response classes and service-account JWT authentication: Pub/Sub, Speech-to-Text, Translation, Vision, Natural Language, Cloud Storage, BigQuery Storage and Vertex AI.
 [+] : New Demos in the folder "Demos/21.GRPC" showing the gRPC client (a generic client) and the Google Cloud service interfaces (Pub/Sub, Speech-to-Text, Translation, Vision, Natural Language, Cloud Storage, BigQuery and Vertex AI).
 [+] : New Kafka client component (TsgcWSPClient_Kafka): native Apache Kafka client that speaks the binary Kafka wire protocol over raw TCP. 
 [+] : New Demo in the folder "Demos/02.WebSocket_Protocols/13.Kafka" showing the main features of the Kafka client: connect, produce, subscribe and poll, topic administration and offset management.
 [+] : New native Android TLS backend (iohAndroidTLS): runs TLS through the platform javax.net.ssl.SSLEngine via JNI, so Android apps deploy no OpenSSL libraries (no libssl.so / libcrypto.so). Validates against the Android system trust store with hostname verification, negotiates TLS 1.3 and supports ALPN on Android 10 (API 29) and later. Selected per platform through TLSOptions.IOHandler and uses the same TLSOptions API (VerifyCertificate, RootCertFile, CertFile, Password, ALPNProtocols). Requires Rad Studio XE8+.
 [+] : New native Apple TLS backend (iohAppleTLS) for iOS and macOS: runs TLS through the operating system, so apps deploy no OpenSSL .dylib. Auto-selects Network.framework (TLS 1.3) on macOS 10.14+ and iOS 12+ and falls back to Secure Transport (TLS 1.2) on older systems. Uses the system trust store with SNI and hostname verification, exposes the OnAppleTLSVerifyPeer event for custom validation, and supports a custom CA (RootCertFile), client certificate / mutual TLS (CertFile + Password) and ALPN. Requires Rad Studio XE6+.
 [+] : New Setup option "Include Resources": uncheck during installation to undefine SGC_RESOURCES in sgcVer.inc before package compilation, so the embedded JS resource is excluded, reducing the size of the apps.
 [+] : New sgcKEM_MLKEM768_Encapsulate and sgcKEM_MLKEM768_Decapsulate: ML-KEM-768 post-quantum encapsulation/decapsulation primitives (OpenSSL 3.5+).
 [+] : New sgcKEM_ECDH_P256_Encapsulate and sgcKEM_ECDH_P256_Decapsulate: ECDH-as-KEM over P-256 (NID_X9_62_prime256v1). Accepts a 65-byte uncompressed public key (Encapsulate) or 32-byte raw private scalar (Decapsulate), returns a 65-byte ephemeral-public-key ciphertext and 32-byte shared secret. Same TBytes API shape as the ML-KEM-768 pair so apps can switch between classical and post-quantum KEMs without code changes.
 [+] : New unit sgcSSL_AEAD with generic AEAD primitives sgcAEAD_Encrypt and sgcAEAD_Decrypt. Supports AES-128-GCM, AES-256-GCM and ChaCha20-Poly1305 via the TsgcAEAD_Cipher enum, accepts caller-supplied 12-byte nonce and arbitrary AAD, with 16-byte authentication tag appended to the ciphertext. Designed for use after KEM Decapsulate + HKDF in hybrid post-quantum / classical handshakes where the existing AES-256-GCM helpers in sgcSSL_E2EE are insufficient (no AAD, random IV).
 [+] : New sgcAEAD_EncryptPrefixed and sgcAEAD_DecryptPrefixed: convenience wrappers that produce/consume the self-contained "nonce(12) || ciphertext || tag(16)" blob layout used by Bouncy Castle GCM, JOSE A256GCM, libsodium crypto_aead_* and most HPKE-style wire protocols. EncryptPrefixed generates a fresh random 12-byte nonce via RAND_bytes; DecryptPrefixed slices the leading 12 bytes off the blob as the nonce.
 [+] : New TsgcWebSocketFirewall BotDetection: IP-based bot classification (verified search-engine crawlers, datacenter/hosting ranges, blocklisted IPs) using known-bot CIDR ranges, datacenter ASN ranges, forward-confirmed reverse DNS (FCrDNS) and DNSBL lookups. Classify-only: results are exposed through the new OnBotDetected event and GetBotClassification method without blocking connections.
 [+] : Improved Firewall demo (Demos\04.WebSocket_Other_Samples\13.Firewall): new "Bot Detection" tab to configure known-bot ranges, datacenter detection, reverse DNS verification and DNSBL zones, with a live "Classify IP" tester.
 [+] : New TsgcWebSocketFirewall IPv6 support: blacklist and whitelist CIDR matching now works for IPv6 addresses and ranges up to /128, GeoIP loads the GeoLite2 IPv6 country blocks, the bot-range database accepts IPv6 CIDR ranges, and bot detection resolves IPv6 reverse DNS and DNSBL (ip6.arpa) lookups. Addresses are normalized (IPv4-mapped, compressed and zone forms) so a client is tracked consistently across spellings. IPv4 behaviour is unchanged.
 [+] : New STDIO transport for the MCP server and client. The MCP server can now run over standard input/output through the new TsgcAI_MCP_Server_Stdio host, so it can be spawned as a local subprocess by MCP clients.
 [+] : New MaxMessageSize property in the WebSocket servers (default 64 MB, 0 = unlimited) to limit the maximum message size.
 [+] : New SecurityOptions.EnforceWebSocketVersion (reply 426 when Sec-WebSocket-Version is not 13) and SecurityOptions.ValidateWebSocketKey (reject an invalid Sec-WebSocket-Key), both enabled by default.
 [+] : New MaxRequestBodySize property in TsgcWebSocketHTTPServer (default 64 MB, 0 = unlimited): rejects oversized HTTP request bodies to prevent memory exhaustion.
 [+] : New StrictRequestParsing property in TsgcWebSocketHTTPServer (default True): rejects an HTTP request that includes both Content-Length and Transfer-Encoding headers (request smuggling).
 [+] : New HTTP/2 Rapid Reset (CVE-2023-44487) protection: per-connection limits on RST_STREAM and control frames and a default maximum of 100 concurrent streams; abusive connections are closed with GOAWAY. 

 [*] : Fixed IPv6 CIDR matching in the TsgcWebSocketFirewall blacklist and whitelist: an IPv6 CIDR (for example 2001:db8::/32) was evaluated with IPv4 32-bit math and collapsed to zero, so it matched every IPv6 client. A whitelist entry then admitted all IPv6 connections and a blacklist entry blocked all of them. CIDR matching is now version-aware.
 [*] : Fixed path traversal in TsgcWebSocketHTTPServer static file serving (HTTP/1.x and HTTP/2): a URL containing "../" could read files outside DocumentRoot. The resolved path is now canonicalized and rejected when it escapes the document root.
 [*] : Fixed possible HTTP response header injection (CRLF) in TsgcWebSocketServer_HTTPAPI: CR and LF characters are now stripped from response header values such as Location, ETag and Server.
 [*] : Fixed cross-thread use-after-free in TsgcIdSSLIOHandlerSocketSChannel (SChannel SSL): Readable and RecvEnc now access SSL.Handle inside the SSL critical section (DoEnterCS/DoLeaveCS), matching SendEnc/Connected/CloseSSL and preventing a race when another thread closes the connection mid-read.
 [*] : Fixed memory leak in TsgcWebSocketServer_HTTPAPI (HTTP.sys server): client disconnections that arrived as failed IOCP completions were silently discarded, so connection objects accumulated and were only released when the server component was destroyed.
 [*] : Fixed WebSocket frame parsing when a frame header arrives split across TCP segments under high throughput. The fixed-size header fields (16-bit/64-bit extended payload length and the 4-byte mask key) are now read in full before being parsed, instead of indexing a read buffer that held fewer bytes than requested. With range checking disabled this could yield a corrupt payload length and drop or garble the message. (Thanks to Jacques for the fix).
 [*] : Fixed possible Denial of Service in TsgcWebSocketServer, TsgcWebSocketHTTPServer and TsgcWebSocketServer_HTTPAPI (http.sys): a client could exhaust server memory with oversized messages, endless message fragmentation or a permessage-deflate "zip-bomb". Messages are now bounded by a maximum size and rejected (close 1009) when exceeded.
 [*] : Fixed 64-bit WebSocket frame length parsing: a length with the high bit set is now rejected instead of being truncated.
 [*] : Fixed TsgcWebSocketServer_HTTPAPI (http.sys) not enforcing client frame masking: per RFC 6455 the server now closes a connection (close 1002) when a client sends an unmasked data frame, matching the other WebSocket servers.
 [*] : Fixed Bug TIdSSLIOHandlerSocketOpenSSL: the peer-verification callback could fail open and accept an untrusted certificate even when verification was requested. Enable the new TIdSSLOptions.StrictVerify option to enforce the OpenSSL verification result.
 [*] : Fixed Bug TIdCustomHTTPServer: the chunked transfer-encoding trailer-header loop was unbounded, allowing a memory and CPU exhaustion DoS. It is now bounded by MaximumHeaderLineCount.
 [*] : Fixed excessive memory usage serving static files from DocumentRoot in TsgcWebSocketHTTPServer (HTTP/1.x and HTTP/2). Each request loaded the whole file into memory with a TMemoryStream per connection, so large files or many concurrent downloads could exhaust RAM (for example 100 connections serving a 1 GB file used about 100 GB), and slow-reading clients kept those copies resident. Files are now streamed from disk with a read-only shared TFileStream, so server memory stays flat regardless of file size and connection count.
 [*] : Fixed Options.WriteTimeOut having no effect on Linux and other POSIX platforms. The send timeout (SO_SNDTIMEO) was applied only on Windows, and POSIX expects a timeval rather than a millisecond integer. It is now set correctly on POSIX, so a client that reads its response very slowly no longer blocks a server thread indefinitely.
 [*] : Fixed wrong MQTT 5.0 property identifiers in TsgcWSPClient_MQTT: the Subscription Identifier property in PUBLISH packets was written as 0x11 (Session Expiry Interval) instead of 0x0B, and the Server Reference property in DISCONNECT packets was written as 0x22 (Topic Alias Maximum) instead of 0x1C, so strict MQTT 5.0 peers could misparse or reject the packets.
 [*] : Fixed Bug TsgcWSPClient_STOMP (and the STOMP broker clients): with the default HeartBeat settings (Enabled = True, Outgoing = 0) the client flooded the server with heart-beat frames, because on connect the WebSocket client heartbeat interval was set to 0 seconds and the timer fired continuously.
 [*] : Fixed TsgcWSPClient_AMQP1 not sending messages larger than the negotiated max-frame-size; the outgoing transfer is now split across multiple frames, so large AMQP 1.0 messages are delivered.
 [*] : Fixed WAMP v1 PUBLISH writing the exclude and eligible lists in the wrong order and the server ignoring them, so the publisher could receive its own event and the exclude/eligible filtering had no effect.
 [*] : Fixed TsgcWSPClient_Files routing file-sent-error notifications to the component instead of the target connection, so the client was never told a transfer failed.
 [*] : Fixed TsgcWSPServer_Presence not freeing empty channels (DeleteChannel was a no-op), so channels accumulated for the lifetime of the server.
 [*] : Fixed E2EE EC public keys being emitted with explicit curve parameters instead of the named-curve form, which strict importers rejected; OpenSSL reads both forms.
 [*] : Fixed the Server-Sent Events fallback sending the retry value multiplied by 1000 (about 50 minutes for the 3000 default); the configured value in milliseconds is now sent unchanged.
 [*] : Fixed TsgcSTUNClient building the transaction id from a low-entropy ASCII range; it now uses a full 96-bit cryptographically-random transaction id.
 [*] : Fixed TsgcTURNClient ChannelData length field including the padding bytes, which broke interop with standard TURN servers; the length now excludes padding per RFC 5766.
 [*] : Fixed TsgcWSAPI_Bybit option market using swapped production and testnet stream hosts.
 [*] : Fixed TsgcWSAPI_Kraken spot subscriptions producing malformed JSON when a reqId was set; the reqId is now appended instead of overwriting the message head.
 [*] : Fixed TsgcWSAPI_MEXC mini-tickers stream never being created due to an inverted check, so mini-ticker subscriptions returned no data.


 [/] : Removed TsgcWSAPI_FXCM component and the sgcWebSocket_API_FXCM unit (FXCM ForexConnect/REST/streaming API client). FXCM has retired its public trading API.






## 2026.5.0: 2026 May

 [+] : New TsgcWSRateLimiter component: drop-in rate limiter for WebSocket/HTTP servers. Supports Token Bucket, Sliding Window and Fixed Window strategies, with PerIP / PerAPIKey / PerUser / PerEndpoint rules, daily/monthly quotas, and burst protection.
 [+] : New TsgcWSCircuitBreaker component: client-side circuit breaker that protects outbound HTTP calls made through any TsgcHTTPAPI_client subclass. When a target host (e.g., api.openai.com) starts failing, the breaker opens and subsequent calls fail fast in microseconds instead of hanging on timeouts.
 [+] : New TsgcWSAPIKeyManager component: full lifecycle manager for API keys - IssueKey, ValidateKey, RevokeKey, RotateKey (with grace period).
 [+] : New Demos for the 3 new infrastructure components, located in Demos\04.WebSocket_Other_Samples - 14.RateLimiter, 15.CircuitBreaker and 16.APIKeyManager. Each demo embeds a TsgcWebSocketHTTPServer plus a TsgcWebSocketClient, wires the new component to the server property, and demonstrates automatic connection / message rejection under flood, failure or unauthorized scenarios, with a live stats timer and event log.
 [+] : New TsgcWSAPI_Forex component: supports unified REST + streaming for Forex.com.
 [+] : New Demo for Forex.com: GUI demo in "Demos\05.Crypto\22.Forex" covering login, connectivity ping, live market watch, positions, active orders, trade history, stop/limit history and simulate trade, with credentials persisted to sgcForexDemo.ini.
 [+] : New TsgcWSPClient_Lightstreamer component: generic Lightstreamer TLCP 2.5 client, reusable for any Lightstreamer server (Forex.com, IG Markets, etc.). Implements create_session, bind_session, control (subscribe / unsubscribe) and the LOOP auto-rebind + subscription replay after reconnect.
 [+] : Improved HTTP.sys Server: new FineTune property implementing OperatingMode property with opt-in ompHighPerf mode implementing N workers x M pre-posted async receives (MSDN High Performance pattern). Default ompClassic preserves existing behavior.
 [+] : Improved HTTP.sys Server: THttpServerRequest and THttpServerResponse have been udpated to include more fields. 
 [+] : Improved EPOLL IOHandler (Linux): new properties AcceptBatchSize, WaitTimeoutMS and HandshakeTimeoutMS.
 [+] : Improved EPOLL IOHandler (Linux): EPOLLOUT-driven write backpressure. When send() returns EAGAIN on a partial write, the remaining bytes are captured in a per-connection pending buffer and the socket is re-armed with EPOLLIN|EPOLLOUT; the reactor flushes the tail on the next EPOLLOUT event.
 [+] : Improved IOCP IOHandler (Windows): new ThreadAffinity property (default False) on TsgcIndy_IO_Engine. When enabled, engine threads are pinned round-robin to logical cores via SetThreadAffinityMask, reducing cross-core cache traffic on high-core-count systems.
 [+] : Improved IOCP IOHandler (Windows): new TsgcIndy_IO_EngineMetrics record and readonly Metrics property exposing AcceptsPosted, AcceptsCompleted, ReadsPosted, ReadsCompleted, ActiveConnections, BytesRead and BytesWritten counters. Metrics are maintained by the engine with critical-section-protected increments.
 [+] : Improved IOCP IOHandler (Windows): new SendBufferSize, ReceiveBufferSize and TCPNoDelay properties on TsgcIndy_IOHandler_IO_IOCP. Applied in AfterAccept via setsockopt (SO_SNDBUF, SO_RCVBUF, TCP_NODELAY) so per-connection tuning no longer requires a custom OnConnect handler.
 [+] : Improved IOCP IOHandler (Windows): TsgcPerIoDataPool capacity raised from 256 to 2048, avoiding the GetMem/FreeMem heap fallback under high connection concurrency. Measured +15-18% WebSocket throughput on loopback benchmarks.
 [+] : Improved MCP Server: built-in OAuth 2.1 flow for browser-based connectors (claude.ai). Auto-serves /.well-known/oauth-authorization-server (RFC 8414), /.well-known/oauth-protected-resource (RFC 9728), /oauth/register (RFC 7591 DCR), /oauth/authorize (HTML consent form) and /oauth/token (PKCE S256 + refresh tokens).
 [+] : Improved MCP Server: CORS support with origin reflection and HSTS (Strict-Transport-Security: max-age=31536000) on all responses; OPTIONS preflight returns 204 with full Access-Control-* headers.
 [+] : New sgcKEM_CreateMLKEM768Keys: generates an ML-KEM-768 post-quantum keypair (PEM and raw bytes). 

 [*] : Fixed MCP Server: missing/invalid credentials now return 401 Unauthorized with a WWW-Authenticate: Bearer header pointing at the protected resource metadata, instead of 500 Internal Server Error. Required for OAuth discovery by browser-based MCP clients.
 [*] : Fixed MCP Server: OPTIONS requests no longer hit the JSON-RPC parser (was returning 500 "Invalid jsonrpc Value"). CORS preflight is now handled before authentication and before the MCP body parser.
 [*] : Fixed HTTP.sys Server: context leak on ERROR_MORE_DATA in TsgcHTTPServerAPI.DoExecute. The accept loop now grows the buffer and retries HttpReceiveHttpRequest on the same request id, and releases orphaned contexts on all error paths.
 [*] : Fixed HTTP.sys Server: TsgcWSConnectionServer_HTTPAPI.DoSendHTTP_Response no longer sets HTTP_SEND_RESPONSE_FLAG_MORE_DATA on the final response.
 [*] : Fixed IOCP IOHandler (Windows): TsgcIndy_IO_Engine_IOCP_Base.DoStopThreads was calling WaitForMultipleObjects on an array of DWORD thread IDs (FThreadsId) instead of thread HANDLES.
 [*] : Fixed IOCP IOHandler (Windows): pending I/O operations on sockets are now cancelled on shutdown and on per-socket close.
 [*] : Fixed IOCP IOHandler (Windows): replaced the fragile Overlapped.Internal = STATUS_PENDING probe in DoFreePerIoData with an explicit Completed: Boolean flag on TsgcPerIoData.
 [*] : Fixed IOCP/EPOLL IOHandler worker pool: TsgcIndy_IO_WorkOpThread.Run issued sleep(1) on every iteration, including after a task was processed, capping each worker at ~1000 ops/s even when the queue had backlog.
 [*] : Fixed MCP Server: tool descriptions, prompt messages and resource contents containing non-ASCII characters broke MCP client connections because the JSON body was not ASCII-safe while the HTTP header declared charset=utf-8.
 [*] : Fixed HTTP API request body decoding: TsgcWSComponent_Server.DoHTTPRequestAPI was reading the inbound HTTP body via ReadStringFromStream without specifying an encoding, defaulting to ASCII. Any non-ASCII byte was substituted with '?' before reaching event handlers.
 [*] : Fixed MCP Server: tool, prompt, resource, root, template, completion-ref and completion-argument 'name' fields containing non-ASCII characters were emitted/read as raw UTF-16 code points rather than JSON \uXXXX escapes.
 [*] : Fixed HTTP/2 WebBrokerBridge: "Invalid pointer operation" on sgcFree(oResponse) in TsgcWSHTTPServer.OnHTTP2RequestEvent when DataSnap REST handled an HTTP/2 HEADERS-only frame.





## 2026.4.0: 2026 April

 [+] : Added Support for Rad Studio 13.1: the new platform WinARM64EC is supported.
 [+] : New TsgcWSFirewall component: full-featured firewall for WebSocket servers with IP blacklist/whitelist (CIDR support), brute force protection with auto-ban, SQL injection detection, XSS detection, rate limiting, and flood protection.
 [+] : New Demo for Server Firewall: shows the main features of the new Firewall and is located in the folder: "Demos\04.WebSocket_Other_Samples\13.Firewall".
 [+] : New Demo for HTTP/2 Large File Transfer: server + client demo for testing 1GB+ file downloads via HTTP/2, located in "Demos\20.HTTP_Protocol\13.HTTP2_LargeFile_Transfer".
 [+] : New HTTP/2 debug logging: frame send/receive, WINDOW_UPDATE increments, and streaming chunk reads are logged via LoggerPro when {$DEFINE SGC_DEBUG} is enabled in sgcVer.inc. 
 [+] : Improved MQTT Client: new property RcvMsg to get access to the latest MQTT message received from the server.
 [+] : New TsgcTCPClient component: full-featured TCP client based on the WebSocket client infrastructure, supporting TLS/SSL, proxy, watchdog and protocol integration. Protocols (MQTT, AMQP, STOMP, WAMP, etc.) can now use either TsgcTCPClient or TsgcWebSocketClient via their Client property. 
 [+] : New OAuth2 Client Token Revocation support (RFC 7009): Revoke() method with OnBeforeRevokeToken, OnAfterRevokeToken, and OnRevokeTokenError events.
 [+] : New OAuth2 Client Token Introspection support (RFC 7662): Introspect() method with OnBeforeIntrospectToken, OnAfterIntrospectToken, and OnIntrospectTokenError events.
 [+] : New OAuth2 Client Device Authorization Grant (RFC 8628): auth2DeviceCode grant type with automatic polling, OnDeviceCode and OnDeviceCodeExpired events.
 [+] : New OAuth2 Server Token Revocation endpoint (RFC 7009): /sgc/oauth2/revoke with OnOAuth2AfterRevokeToken event.
 [+] : New OAuth2 Server Token Introspection endpoint (RFC 7662): /sgc/oauth2/introspect with OnOAuth2AfterIntrospectToken event.
 [+] : New OAuth2 Server Device Authorization endpoint (RFC 8628): /sgc/oauth2/device and /sgc/oauth2/device/verify with OnOAuth2DeviceAuthorization and OnOAuth2DeviceCodeVerification events.
 [+] : New OAuth2 Server Resource Owner Password Credentials grant handling (password grant_type).
 [+] : New OAuth2 Server Device Code token exchange (urn:ietf:params:oauth:grant-type:device_code grant_type).
 [+] : New OAuth2 Client DPoP support (RFC 9449): sender-constrained tokens via DPoPOptions with ES256/RS256 signing, automatic DPoP proof JWT generation, JWK thumbprint calculation (RFC 7638), and DPoP-Nonce retry handling.
 [+] : New OAuth2 Client DPoP methods: GetDPoPProof() for resource requests, GetDPoPJWKThumbprint() for token binding verification.
 [+] : New OAuth2 Server DPoP support (RFC 9449): DPoP proof validation, JWK thumbprint token binding, token_type DPoP issuance, and OnOAuth2ValidateDPoP event.
 [+] : Improved Deflate extension: the speed has been improved specially for small messages. (Thanks to Michael for the fix).
 [+] : New TsgcWebView2 component: visual VCL wrapper for Microsoft Edge WebView2 with navigation, JavaScript (async/sync/init scripts), cookie management, download control, profile management, print, audio/mute, certificate handling, context menus, favicon, virtual host mapping, screenshot capture, and 20+ events. Supports Delphi 7 through Delphi 13.
 [+] : New Demo for WebView2 Browser: shows navigation, JavaScript execution, cookies, print, mute, clear data, virtual host mapping and event logging. Located in "Demos\50.Other\WebView2_Browser".
 [+] : New Gemini API: Google Gemini integration with Content Generation (with streaming), Vision, Structured JSON Output, Tool Use (function calling), Token Counting, Embeddings, and Model listing.
 [+] : New DeepSeek API: DeepSeek integration with Chat Completions (with streaming), Vision, Tool Use (function calling), and Model listing.
 [+] : New Ollama API: Ollama local LLM integration with Chat Completions (with streaming), Model Management (show, pull, delete, list tags), and Embeddings.
 [+] : New Grok API: xAI Grok integration with Chat Completions (with streaming), Vision, Tool Use (function calling), and Model listing.
 [+] : New Mistral API: Mistral AI integration with Chat Completions (with streaming), Vision, Structured JSON Output, Tool Use (function calling), Embeddings, and Model listing.

 [*] : Fixed HTTP/2 server-side streaming for large responses: Eliminates out-of-memory crashes when serving large files and reduces peak server memory.
 [*] : Fixed HTTP/2 client-side memory reallocation when receiving large responses: payload buffer now uses a capacity growth strategy with platform-specific caps (128 MB on Win32, 1 GB on Win64) instead of reallocating on every DATA frame.
 [*] : Fixed HTTP/2 SSL write deadlock on large file transfers: WINDOW_UPDATEs are now queued and flushed between read iterations instead of being written inline during frame processing, preventing both client and server from blocking simultaneously on SSL_write.
 [*] : Fixed HTTP/2 Integer overflow for files larger than 2 GB: changed FrameLength, Offset, WindowSize, PayLoadCapacity, ReadWindowSize, and flow control accumulators from Integer to Int64.
 [*] : Fixed HTTP/2 stream state: RST_STREAM frames received on idle streams (after stream cleanup) now gracefully transition to closed instead of raising a PROTOCOL_ERROR.
 [*] : Fixed HPACK encoder: GetBestMatchingIndex now correctly returns static table name-only matches, preventing compression errors on HTTP/2 connections.
 [*] : Fixed HPACK encoder: Huffman bit mask uses correct shift-left operation.
 [*] : Fixed HPACK decoder: byte count and available bytes calculations now correctly account for the buffer offset.
 [*] : Fixed SetBytesFromInteger: intermediate byte extractions now masked with $FF to prevent range check errors on values like WINDOW_UPDATE increments.
 [*] : Fixed typed pointer incompatibilities when compiling with the option active "Typed @ operator".
 [*] : Fixed JWT RSA signing: vLength parameter in DoSignRSA was declared as Integer instead of TIdNativeUInt, causing potential stack corruption on 64-bit platforms. (Thanks to Gabriel for the fix).
 [*] : Fixed Win64 pointer truncation in sgcHTTP_API_OpenAI: mciSendCommand calls used Cardinal() cast on pointers, replaced with NativeUInt().
 [*] : Fixed OAuth2 Server: SetOAuth2Options memory leak fixed.
 [*] : Fixed AWS Signature V4: fixed query string parameter sorting in canonical request. 
 [*] : Fixed Bitfinex access violation when unsubscribe from a channel.
 [*] : Fixed memory leaks in Indy Servers caused by thread-unsafe lazy initialization of FSpecifications and FConnections fields. Concurrent Indy worker threads could race on creation, orphaning instances. 

 [/] : The OnMQTTPublishEx event has changed the signature adding a new parameter aMessage of type TsgcWSMQTTMessage.




## 2026.3.0: 2026 March

 [+] : New MQTT OnMQTTPublishEx event: provides the published message payload as a TsgcWSMQTTPublishData object with Value (string), Bytes (TBytes) and Stream (TMemoryStream) properties.
 [+] : Indy Servers now support SChannel, so OpenSSL libraries are no longer needed on Windows for TLS.
 [+] : New OpenAI: Added Responses API, Fine-Tuning Jobs, Audio Speech, Batch and Uploads APIs, modernized Chat Completions, and new demo tabs for all features.
 [+] : New Anthropic Claude API: Added Messages (with streaming), Vision, Tool Use, Extended Thinking, Documents/PDF, Citations, Prompt Caching, Structured JSON Output, Web Search, MCP Server integration, Code Execution, Files, and Message Batches APIs, and new demo tabs for all features.
 [+] : New AMQP 0.9.1 Features: Basic.Nack, Exchange-to-Exchange bindings, Publisher Confirms, Connection.Blocked/Unblocked, OAuth/JWT token refresh, and incoming Basic.Ack handling.
 [+] : The Crypto API Demo has been split into multiple demos, one for each API provider.
 [+] : New Bitget REST & WebSocket API.
 [+] : New Gate.io REST & WebSocket API.
 [+] : New Deribit REST & WebSocket API.
 [+] : New Crypto.com REST & WebSocket API.
 [+] : New HTX REST API (Huobi rebrand).
 [+] : Updated Huobi WebSocket API URLs from huobi.pro to htx.com. 
 [+] : Updated Binance REST & WebSocket API.
 [+] : Updated Bitstamp REST API.
 [+] : Updated Huobi WebSocket API.
 [+] : Updated CEX Plus WebSocket API.
 [+] : Updated BitMEX REST & WebSocket API.
 [+] : Updated OKX WebSocket API.
 [+] : Updated Bybit REST & WebSocket API.
 [+] : Updated Kraken REST API.
 [+] : Updated Coinbase REST API.
 [+] : Updated 3Commas REST API.
 [+] : Updated KuCoin REST & WebSocket API.
 [+] : Updated MEXC REST & WebSocket API.
 [+] : Updated Discord API from version 6 to version 10.
 [+] : Updated component icons.

 [*] : Fixed Setup Error: Installing sgcWebSockets for Delphi 7 with sgcIndy raised an error about IdFIPS.pas.
 [*] : Fixed AMQP 0.9.1: Parameter ordering, field-table encoding, spec-incorrect data types, missing channel IDs, read-loop data loss, and a thread-safety race condition.
 [*] : Fixed AMQP 1.0: Serialization errors, missing frame fields, multiple memory leaks, connection state handling, heartbeat activation, and thread safety.
 [*] : Fixed some minor memory leaks.




## 2026.2.0: 2026 February

 [+] : Improved OpenAPI Parser: Now allows converting OpenAPI files to Pascal using the command line.
 [+] : Improved OpenAPI Parser: The executable is now compiled for Win32 and Win64. A new folder, "bin64", has been added for the 64-bit version.
 [+] : New OpenAPI Library: sgcOpenAPI.dll allows you to call the OpenAPI parser from a DLL.
 [+] : New OpenAPI API: When creating the Pascal interface file, you can now modify its content using a custom sgcOpenAPI_API.dll.
 [+] : New Demo for OpenAPI API: The folder "Demos\sgcOpenAPI_api" includes a Delphi demo of the sgcOpenAPI API.
 [+] : Improved E2EE Components: Added support for group messages using group sender keys.
 [+] : Updated E2EE Demo: Added new options such as creating groups, joining, leaving, deleting, and sending group messages.
 [+] : Improved OpenAI RealTime Client: The new method AppendInputAudioBuffer allows sending audio streams manually without using an Audio Recorder component.
 [+] : Added sgcWebSocket.module.js as an ES module version (thanks to Francesco for the file).

 [*] : Fixed Indy Server bug: Authentication was not working even though it was enabled.
 [*] : Fixed Indy Client bug: The ReadTimeOut property was not set properly when using TLS 1.3+ (thanks to Francesco for reporting it).
 [*] : Fixed some minor setup bugs.
 [*] : Fixed HTTP/2 Client demo: Now waits until the client has disconnected before processing a new request.





## 2026.1.0: 2026 January

 [+] : New Protocol E2EE (End-to-End Encryption) where messages are encrypted end-to-end and only the communicating clients can read them. Available only for All-Access subscribers.
 [+] : New Demo E2EE: in the folder "Demos\02.WebSocket_Protocols\12.E2EE" there is a demo showing how the Server/Client E2EE work.
 [+] : Added support for Lazarus 4.4
 [+] : Improved AMQP1 Client: added support for AMQP 1.0 over WebSockets.
 [+] : Improved AMQP1 Client: added support for CBS Authentication (SAS Tokens and JWT).
 [+] : Updated the AMQP1 Demo to show how to connect to Azure Service Bus using AMQP1 over WebSockets and using CBS Authentication.
 [+] : Improved Setup: now compiles and installs the sgcWebSockets package in Lazarus (before only extracts the files).

 [*] : Fixed Bug MCP: when compiling the unit sgcMCP_Classes.pas under Lazarus an error was raised.
 [*] : Fixed Bug Indy Server: access violation when running on Linux64.
 [*] : Fixed Bug SignalR: when using Cookie authentication, the websocket connection was not using the cookie value.
 [*] : Fixed Bug Setup: when installing sgcWebSockets with sgcIndy already installed under Delphi 7, the sgcIndy path was not found.
 [*] : Fixed Bug Lazarus: when compiling the package there was an error in the sgcProtoBuf unit name.
 [*] : Fixed Bug sgcSSL_WinSSPI: some definitions may cause an ambiguous error when compiling on cbuilder.





## 2025.10.0: 2025 November

 [+] : New Component TsgcWSAPIClient_MCP implements the MCP Cilent specification.
 [+] : New Demo MCP Client showing the main features of the MCP Client, can be found in the folder "Demos\15.AI\03.MCP\02.MCP_Client". 
 [+] : Improved MCP Server: now supports Streamable HTTP.
 [+] : Improved MCP Server: now supports Authentication using Custom Headers or API Key.
 [+] : New Client Component TsgcWSAPI_MEXC: Implements the WebSocket & HTTP API Spot API from MEXC (centralized cryptocurrency exchange).
 [+] : New Client Component TsgcWSAPI_MEXC_Futures: Implements the WebSocket & HTTP API Futures API from MEXC (centralized cryptocurrency exchange).
 [+] : Updated CryptoAPI demo showing the main features of the MEXC API. It's in the folder "05.Crypto\01.CryptoAPI".
 [+] : Improved Setup: now the uninstaller is digitally signed.
 [+] : Improved HTTP Server: new event OnHTTPUploadBeforeCreatePostStream which is fired before the stream is created.
 [+] : Improved HTTP Client: new property keep-alive to maintain the connection alive between requests.
 [+] : Improved Google Cloud Clients: new property TLSOptions to customize the secure connection options. Apply to Google Cloud FCM, Calendar and PubSub Clients.

 [*] : Fixed Bug MCP component: when returning a json-rpc error, the node error was not set properly.
 [*] : Fixed Bug MultipartFormData: when HTTPUploadFiles.RemoveBoundaries was true and the file size was zero, the file was created with the boundaries included. 
 [*] : Fixed Memory Leak in the STOMP ActiveMQ Client Component.
 [*] : Fixed Memory Leak in the STOMP RabbitMQ Client Component.
 [*] : Fixed Bug Server: when KeepAlive property was active, the built-in javascript libraries return an error 404.
 [*] : Fixed Bug Server: when Authentication was not enabled, if the client send a request with an Authorization header, by default the connection was closed.
 [*] : Fixed Bug ServerSentEvents: when sending multiple messages the headers were included in the message.
 [*] : Fixed Bug ServerSentEvents: the initial message was sent twice.







## 2025.9.0: 2025 October

 [+] : New Component TsgcWSAPIServer_MCP implements the MCP Server specification, currently supports: Tools, Prompts and Resources requests.
 [+] : New Demo MCP Server showing the main features of the MCP Server, can be found in the folder "Demos\15.AI\03.MCP\01.MCP_Server".
 [+] : Updated the Telegram libraries to the version 1.8.54. (Windows, Android, iOS, Linux64 and OSX).
 [+] : Updated sgcIndy to the latest version.
 [+] : Improved setup: added a remainder to configure the platform in the IDE if unavailable. (Thanks to Peter for the suggestion).
 [+] : Improved sgcIndy Setup: added the parameter "/debug" to get a warning message if there is any error while compiling the Embarcadero package.

 [*] : Fixed Bug Telegram: the android64 library requires to be built with a 16KB page size from November 2025.
 [*] : Fixed Bug sgcIndy: the cipherlist is now set before loading the certificates to allow to set for example the security level. (Thanks to Preben for the fix)
 [*] : Fixed Bug sgcIndy: Cannot assign a TIdSSLX509Checks to a TIdSSLOptions_Internal. 
 [*] : Fixed Bug sgcIDE Expert: the form was not displayed with the correct size.
 [*] : Fixed Bug OnHandshake event: UTF-8 characters were not encoded properly when adding new headers.
 [*] : Fixed Bug AMQP: the internal function sgcWriteAMQPFieldTable was passing all the values as a string.
 [*] : Fixed Bug TsgcOpenAIClass.DoReadDouble: when the decimal separator wasn't set to '.' the returned value was invalid. (Thanks to Pierre for the fix)
 [*] : Fixed Bug OpenAPI Parser: optional Boolean parameters can't send a False parameter in the querystring, now the boolean has been replaced by TsgcOpenAPIBoolean.
 [*] : Fixed Bug DataSnap HTTP/2 Server: OPTION requests where not processed and the connection was not closed.
 [*] : Fixed Bug Indy Server: if Authentication.Basic was enabled, the server didn't return the Basic Realm when the Authentication header was wrong.

 [/] : OpenAPI: Optional Boolean Parameters have been replace by the enum TsgcOpenAPIBoolean = (oapiBoolNull, oapiBoolFalse, oapiBoolTrue).




## 2025.8.0: 2025 September

 [+] : Added Support for Rad Studio 13 Florence.
 [+] : The WebAuthn Server Component passed the full FIDO Conformance Test using the Conformance Self-Validation Testing tool. 
 [+] : Improved Servers: Added a new Authorization protocol in the property Authentication.WebAuthn.
 [+] : Improved WebAuthn: new event "OnWebAuthnUnauthorized" which is called when a request is not authorized and will be disconnected here you can configure which endpoints require WebAuthn Authentication and which not.
 [+] : Improved sgcIndy Setup: the Embarcadero IP Abstraction units are now compiled with the sgcIndy version installed. 
 [+] : Improved sgcIndy Setup, Added support for CBuilder 64-bits IDE.
 [+] : Improved sgcIndy Setup: Added the Platform "Windows 64-bit Modern" for CBuilder.
 [+] : Improved IOCP Server when using TCP Connections. If in the event OnTCPConnection, the property Connection.Transport is set to trpTCP, the event OnConnect will be fired instead of waiting till receive the first message.

 [*] : Fixed Bug Setup, when installing the enterprise edition without the custom indy version returned the error E2003: Undeclared identifier: 'DoProcessHTTP'.
 [*] : Fixed Bug sgcIndy: when installing community edition and then the registered version, the original indy package was not restored when sgcIndy was uninstalled.
 [*] : Fixed Bug sgcIndy: the setup wasn't disabling the package msedge when setting compatibility mode to true.
 [*] : Fixed Bug sgcIndy: after uninstalling sgcIndy an rtl.bpl error was raised after closing the IDE.
 [*] : Fixed Bug sgcIndy: when multiple editions were installed a Runtime error maybe raised when opening the IDE. 
 [*] : Fixed Bug sgcIndy: when compiling IdSSLOpenSSLHeaders_static for iOS, error E2009: Incompatible types: "Calling conventions differ".

 [/] : Renamed CERT_NAME_BLOB to CERTIFICATE_NAME_BLOB in the unit sgcSSL_WinSSPI to avoid name conflict with other libraries.
 [/] : Renamed the property HeartBeat.HearBeatType to HeartBeat.HeartBeatType.





## 2025.7.0: 2025 August

 [+] : Improved WebAuthn: added support for PS256, PS384 and PS512 algorithms.
 [+] : Improved WebAuthn: new property WebAuthnOptions.MDS to configure the Fido Metadata Service.
 [+] : Improved HTTP.SYS: added support for the WebAuthn protocol.
 [+] : Updated the OpenSSL libraries to the version 3.5.1
 [+] : Improved STOMP Protocol: added a new event OnSTOMPPing to handle the pings sent/received.
 [+] : Improved Clients using OpenSSL: new property TLSOptions.OpenSSL_Options.X509Checks to enable validate HostName and IPAddress in X509 Certificates.
 [+] : Improved sgcIndy: new property TIdSSLIOHandlerSocketOpenSSL.SSLOptions.X509Checks to enable validate HostName and IPAddress in X509 Certificates.

 [*] : Fixed Bug WhatsApp: when sending an url or path, the message was not decoded properly.
 [*] : Fixed Bug sgcVer.inc: rearrange some compiler directives to avoid incompatiblities between editions.
 [*] : Fixed Memory Leak WebSocket WinHTTP Client.
 [*] : Fixed Memory Leak Google Calendar Client.
 [*] : Fixed Memory Leak UDP Server and Client.
 [*] : Fixed Memory Leak ByBit Client.
 [*] : Fixed Memory Leak HTTP.SYS Server.
 [*] : Fixed Memory Leak when using the SGC_HTTPAPI_STATIC compiler directive.
 [*] : Fixed Memory Leak MQTT Client.
 [*] : Fixed Memory Leak WebAuthn Server Component.
 [*] : Fixed Bug setup, when installing for CBuilder 12 the setup failed to install the components for the IDE 64bits.
 [*] : Fixed some minor bugs.




## 2025.6.0: 2025 June

 [+] : Improved OpenAI Assistant: new event OnFunctionCall which allows to interface OpenAI models with your code, database, applications...
 [+] : Updated the OpenAI Assistant Demo with a new Assistant "Delphi Weather Bot" showing how it works.
 [+] : Improved Whatsapp API: updated api to v20.
 [+] : Improved Whatsapp API: new method SendMessageReaction.
 [+] : Improved Whatsapp API: the SendMessage methods now include a new optional parameter called options where you can reply to a message passing the message-id.
 [+] : Improved Telegram API: added more than 100 new methods to the api.
 [+] : Improved Google PubSub Client: updated to the latest version the methods for projects subscriptions and topics.
 [+] : Improved RSA unit: the function sgcRSA_GetPRSAFromCOSE only works for openssl 1.1+.
 [+] : Improved WebAuthn: added support for the algorithm EDDSA.
 [+] : Improved WebAuthn: new Event OnWebAuthnRegistrationValidateCertificate, allows to verify the certificate with your own methods or assign a root certificate if not provided.
 [+] : Improved WebAuthn: new Event OnWebAuthnMetadata, allows to provide a custom metadata if the authenticator is not found in the Fido MDS file.
 [+] : Improved WebAuthn: new property WebAuthnOptions.DefaultOptions to provide the default values of the Registration and Authentication Options Request.
 [+] : Improved WebAuthn: included more validations for the certificate fields.
 [+] : Improved WebAuthn: now validates the type of the request json fields.
 [+] : Improved OpenAPI Parser: added support for OneOf elements.
 [+] : Improved sgcIndy: new function sgcIdSSLOpenSSL.GetOpenSSLErrors to obtain the list of the latest errors.
 [+] : Improved setup: now supports Rad Studio 64bits for sgcWebSockets Basic editions.
 [*] : Improved SignalRCore: added the SignalRCore.SkipNegotiation property to skip connection negotiation and establish a WebSocket connection directly.


 [*] : Fixed Bug CBuilder: calling the method SendMessage on some components returned an error.
 [*] : Fixed Bug SignalR: the initial http request was creating a log file by default.
 [*] : Fixed Bug using the method RegisterProtocol(aProtocol: string) if this was called before assigning the events, the events were not called.
 [*] : Fixed Bug internal method was calling OnMessage event instead of OnError.
 [*] : Fixed Bug sgcIndy: function RSA_set0_key, only is required for openssl 1.1+.
 [*] : Fixed Bug sgcIndy: decoding UTC DataTime.
 [*] : Fixed Bug sgcIndy: if EVP_PKEY_base_id function is not available use the EVP_PKEY_is_a function instead.
 [*] : Fixed Bug Binance: the websocket messages were not processed. (Thanks to Alex for the fix).
 [*] : Fixed Bug Indy Server: if Authentication was enabled, if the HTTP Request hasn't any authentication, the connection was accepted although Authentication.AllowNonAuth was set to false.
 [*] : Fixed Bug JWT: some internal openssl objects were not properly destroyed after signing or validating.
 [*] : Fixed Bug JWT: error evaluating if the algorithms TIdHashSHA384 or TIdHashSHA512 were available.
 [*] : Fixed Bug AI Components: removed some memory leaks while destroying the internal objects.
 [*] : Fixed Bug TsgcHTTP1Client: when calling an Async method, the default request was not assigned internally.




## 2025.5.0: 2025 May

 [+] : Improved WebAuthn Server: new events to handle better the Options request/response for the Registration and Authentication flows. 
       - OnWebAuthnRegistrationOptionsRequest: allows to cancel an undesired registration request.
       - OnWebAuthnRegistrationOptionsResponse: allows to customize the registration options response.
       - OnWebAuthnAuthenticationOptionsRequest: the parameter CredentialRecord has been changed to a list of CredentialRecords.
       - OnWebAuthnAuthenticationOptionsResponse: allows to customize the authentication options response.
 [+] : Improved the WebAuthn demo to show how to store multiple credential records.
 [+] : New Component TsgcWSAPI_OpenAI, implements OpenAI Realtime API Beta using the websocket protocol as transport.
 [+] : New Demo showing the main features of the TsgcWSAPI_OpenAI client component. It's located in the folder "Demos\15.AI\01.QuickStart\06.RealTime".
 [+] : New Component TsgcAudioRecorderWave, allowing to record microphone audio as PCM16 and store into a wave file.
 [+] : Improved Setup: added a new About button when the setup has finished with the credits.	   
 [+] : Improved TsgcHTTPRequest Class: added the property Headers which contains all the HTTP Headers of the request.

 [*] : Fixed in Server APIs: when http/2 was enabled, the response was empty.
 [*] : Fixed in Server APIs: when using more than one Server API only the last assigned API was working.
 [*] : Fixed Bug MQTT: When reading the MQTT 5 properties, if the size of the packet was 2 bytes or more, the message was not parsed successfully.
 [*] : Fixed Bug MQTT: When reading the Remaining Length of the packet, if was greater than 128, the message was not parsed successfully.
 [*] : Fixed Bug Setup, the third-party libraries were not extracted in the correct folder.

 [/] : Deleted the BlockChain API Component.
 [/] : The event OnWebAuthnAuthenticationRequest has been renamed to OnWebAuthnAuthenticationOptionsRequest.






## 2025.4.0: 2025 April

 [+] : New WebAuthn Server Component: Implements the WebAuthn Server Specification, a web standard for secure, passwordless authentication. Currently in BETA.
 [+] : New WebAuthn Demo: Demonstrates how to register and authenticate using the TsgcWSAPIServer_WebAuthn component. Available in the folder "Demos\20.HTTP_Protocol\12.WebAuthn".
 [+] : WebAuthn Attestation Formats Supported: None, Packed, TPM, AndroidKey, Apple, and FidoU2F.
 [+] : WebAuthn Algorithms Supported: ES256 and RS256.
 [+] : Improved the SGC Protocol Demo "Demos\02.WebSocket_Protocols\01.SGC_Generic_PubSub_Protocol" now includes SSL support and allows configuration of the QoSLevel on both server and client components.

 [*] : Fixed bug in OAuth2 Client: When changing the local server port, the old port was not removed from the bindings list.
 [*] : Fixed bug in WebBroker HTTP/2 Server: The DoBeforeOnCommand function was not properly defined.
 [*] : Fixed bug in AMQP1 Client: When reading a timestamp value, the decoded result was incorrect in some cases.
 [*] : Fixed bug in AMQP1 Client: Reading an empty map resulted in an integer overflow exception.
 [*] : Fixed bug in AMQP1 Client: Binary data was not decoded properly.
 [*] : Fixed bug in AMQP1 Client: When reading a UUID, the internal offset value was not updated correctly.
 [*] : Fixed bug in OpenAI Azure Client: The endpoint used for transcription requests was incorrect.
 [*] : Fixed bug in OpenAI Demo: Located in Demos\15.AI\01.QuickStart\04.ChatGPT. When sending the context of previous requests, failures could occur due to improperly encoded JSON strings.
 [*] : Fixed bug in MultipartFormData: When extracting files, the internal stream was not using UTF-8 encoding.
 [*] : Fixed bug in Setup: When using the /extract command, if the Delphi version was not installed, the extraction process failed.
 [*] : Fixed bug in MQTT Client: memory leak if the component was destroyed before the event OnDisconnect was called.






## 2025.3.0: 2025 March

 [+] : Added Support for Rad Studio 12.3
 [+] : Improved Setup, a new option "Build Rad Studio IDE Win64" allows to install the package for the 64-bit IDE, by default is disabled.
 [+] : Improved TsgcWebSocketClient, when using SChannel there is a new event "OnSChannelVerifyPeer" to validate manually the certificate.
 [+] : Improved HTTPClient, when using SChannel there is a new event "OnSChannelVerifyPeer" to validate manually the certificate. 
 [+] : Improved TCPClient, when using SChannel there is a new event "OnSChannelVerifyPeer" to validate manually the certificate. 
 [+] : Improved OpenAPI Google Demos, when using service account to authenticate if the subject and scope are not defined, a default value is set.
 [+] : Improved TsgcWebSocketClient_WinHTTP, the OnHandshake event is now called before connecting, allowing customization of the WebSocket HTTP headers.
 [+] : Improved HTTP.SYS Server, the reason response code table has been updated to include all possible values.
 [+] : Improved sgcIndy, added two functions: IdOpenSSLSetLoadFuncsCallback and IdOpenSSLSetUnLoadFuncsCallback to load additional openssl functions using the dll already loaded.
 [+] : Improved sgcIndy, new demo LoadCustomFunctions which shows how to use the new callback for loading additional openssl functions.
 [+] : Improved TsgcHTTP1Client, new methods for async requests: GetAsync, PostAsync, PutAsync... the response is received asynchronously in the event OnAsyncResult of the component.

 [*] : Fixed Bug WebPush was not working whe compiling for Win64.
 [*] : Fixed Bug sgcIdSSLOpenSSLHeaders, the method X509_STORE_CTX_free was not properly defined.
 [*] : Fixed Bug sgcIdSSLOpenSSLHeader, the method ECDH_compute_key was not properly defined.
 [*] : Fixed Bug CBuilder error "reference to HRESULT is ambiguous". 
 [*] : Fixed Bug CBuilder error "expected unqualified-id" in the SChannel units.
 [*] : Fixed Bug HTTP.SYS Server, all HTTP responses were sent with a fixed response code 200.
 [*] : Fixed Bug HTTP/2 Demo, the server was only accepting tls1_3 while the client was using tls1_2.




## 2025.2.0: 2025 February

 [+] : Improved Socket.IO Client, new property HandShakeAuthToken to set the authentication token when required.
 [+] : Improved Socket.IO sample, the previous online server has been closed and now has been replaced by a new one.
 [+] : Improved Setup, now if detects the IDE is running aborts the installation until it's closed.
 [+] : Improved HTTP.SYS Server to handle Partial Requests. Added the following properties:
       - THttpServerRequest: Range.
	   - THttpServerResponse: AcceptRanges, ContentRangeStart, ContentRangeEnd and ContentRangeInstanceLength.
 [+] : Improved TsgcWebSocketHTTPServer, new event OnBeforeCommand which allows to customize the response, authorize or not a request... before is done internally.

 [*] : Fixed Bug MQTT Client when using mqtt5 the payload had some invalid characters.
 [*] : Fixed Bug MQTT Client when the connection is over TCP a message received in multiple packets was not decoded properly.
 [*] : Fixed Bug TLS and Android, when using ALPN, the accepted value returned was not properly decoded.
 [*] : Fixed Bug Pusher Client, error processing subscription event without data.
 [*] : Fixed Bug Telegram Client reading the Sender User Id in a group. (Thanks to Michael for the fix).
 [*] : Fixed Bug DataSnap+HTTP.SYS Server the value of the funciton TsgcWebRequestHTTPAPI.GetHeaderValue was returning always empty string.
 [*] : Fixed Bug AMQP1_Client reading an internal TThreadList.
 [*] : Fixed Bug HTTP2 Server, Authentication Basic was not working although it was enabled.






## 2025.1.0: 2025 January

 [+] : Improved OpenAPI Parser, added support for multipart/form-data requests.
 [+] : Improved OpenAI Assistant Demo, now can load the existing assistants created using other tools like openAI Playground.
 [+] : Improved OpenAI Assistant, now supports Streaming the responses using Server-Sent events streams.
 [+] : Improved OpenAI Assistant Demo, there is a new checkbox called Streaming to indicate if the response is using streaming or not.
 [+] : Improved TsgcHTTP1Client, added the following events: OnSSLGetHandler and OnSSLAfterCreateHandler.
 [+] : Improved OpenAPI Client, added the following events: OnSSLVerifyPeer, OnSSLGetHandler and OnSSLAfterCreateHandler.
 [+] : Improved Coinbase Client, updated to support the Advanced Trade WebSocket & REST API.
 [+] : Improved Crypto Demo Sample, to show the main features onf the Coinbase Client.
 [+] : Improved the performance of the WebSocket Extension PerMessage-Deflate. (Thanks to Michael for the patch).

 [*] : Fixed Bug MQTT Client in some cases the MQTT ACK it may not be sent.
 [*] : Fixed Bug TsgcWebSocketClient when using Connect, if the ConnectTimeout was greater than zero, it may appear a conflict.
 [*] : Fixed Bug OpenAPI Parser when the content of the body is "application/x-www-form-urlencoded" it was sending as json by default.
 [*] : Fixed Bug OpenAPI Parser when generating the content as "application/x-www-form-urlencoded" for Dynamic Arrays.
 [*] : Fixed Bug OpenAPI Parser reading class properties where the name contains characters like "[]".
 [*] : Fixed Bug TsgcWSHTTP2WebBrokerBridgeServer component, when using the default content-type, the charset was removed automatically when setting the content-type.
 [*] : Fixed Bug sgcWebSockets Packages from XE5 to D12 the ObjOutput and HppOutput was set to the directory ..\libDXE4 (Thanks to Robert for letting me know).
 [*] : Fixed Bug HTTP/2 Client connecting using openssl 3.0 and tls 1.3.
 [*] : Fixed Bug OpenSSL when setting Version TLS 1.3 and VersionMin TLS 1.2, only TLS 1.2 was available.





## 2024.10.0: 2024 November

 [+] : Improved OpenAI Assistant, now allows to upload files and ask questions about the content of these files.
 [+] : Improved OpenAI Assistant Demo, a new option has been added to upload files. The demo shows how to upload the sgcWebSockets.pdf manual and ask questions about it.
 [+] : Improved sgcIndy Setup, new Option "Avoid Storing New Properties", if set to true, the new properties like APIVersion, LegacyProvider... won't be stored in the dfm files.
 [+] : New property OpenSSL_Options.VersionMin to set which is the minimum version accepted.
 [+] : Added support for Intraweb XVI.
 [+] : Improved Amazon AWS S3 SDK, new method GetObjectAsStream to download the object as a binary stream.

 [*] : Fixed Bug sgcWebSockets setup, when selecting Lazarus install some files where not exported.
 [*] : Fixed Bug OpenAPI Parser when the result is a number.
 [*] : Fixed Bug OpenAPI Client encoding the body as utf-8.
 [*] : Fixed Bug memory leak when receiving fragmented messages, the internal queue object was not destroyed (Thanks to Jasja for letting me know).
 [*] : Fixed Bug sgcIndy setting the minimum accepted tls protocol.
 [*] : Fixed Bug HTTP/2 client when using the HTTP Proxy the SNI host was not set properly and the connection was closed.
 [*] : Fixed Bug OpenAI Client parsing UTF-8 characters.
 [*] : Fixed Bug MQTT Client memory leak when destroying the TsgcWSMQTTUNSUBACK class (Thanks to Robin for letting me know).
 [*] : Fixed Bug WebSocket client would enter a loop if it encountered a 10054 error while connecting.
 [*] : Fixed Bug AMQP1 Client the Hostname was not set properly.
 [*] : Fixed Bug HTTP.SYS Server decoding WebSocket HTTP Headers when the connection comes from a reverse proxy. (Thanks to Corbinian for letting me know).

 [/] : When selecting the openSSL Version tls1_3, now by default only the tls1_3 version will be accepted (before 2024.10.0 release, the tls1_2 was also accepted). 
       There is a new property to set the minimum tls version accepted, OpenSSL_Options.VersionMin.






## 2024.9.0: 2024 October

 [+] : New Component TsgcHTTPGoogleCloud_FCM_Client, Firebase Cloud Messaging (FCM) is a cross-platform messaging solution that lets you reliably send messages at no cost.
 [+] : New Demo "20.HTTP_Protocol\03.Google\03.Google_FCM" which shows how connect to send messages using the Firebase Cloud Messaging Client.
 [+] : Improved OpenAPI Parser, the parser options are included in the output file as comments.
 [+] : Improved OpenAPI Parser, if the openapi file is splitted in multiple schemas the parser can resolve those external schemas and bundle into a single specification file.
 [+] : Improved OpenAPI Parser setup, now supports offline installation.
 [+] : Improved OpenAPI Client, new event OnBeforeRequest which allows to customize the HTTP Request sent.  
 [+] : Improved OpenAPI Client, new property ProxyOptions to configure HTTP Requests through proxies.
 [+] : Impoved TsgcWebSocketClient, new property LogOptions.Raw, if enabled it will save the messages (send/received) in hex format. 

 [*] : Fixed Bug OpenAPI Parser, when the parameter contained an external reference, the parameter was not found when encoding the url.
 [*] : Fixed Bug Indy Server when assigning a OpenSSL IOHandler that inherits from TIdServerIOHandlerSSLBase, the SSLOptions property was not found. (Thanks to Robert for letting me know).
 [*] : Fixed Bug Indy function TIdServerInterceptLogFileConnection.GetConnectionID when connection is not assigned.
 [*] : Fixed Bug sgcIndy when getting the Certificate Signature and openSSL was greater than 1.1.1. 
 [*] : Fixed Bug sgcIndy when using openSSL API 3.0.0 (libraries < 3.2) and trying to load the private key with a password.
 [*] : Fixed Bug AMQP1 Client the LocalMaxFrameSize value was the same than the RemoteMaxFrameSize.
 [*] : Fixed Bug AMQP1 Client when receiving messages greater than the window size the message was not stored properly.




## 2024.8.0: 2024 September

 [+] : Improved OAuth2 Server component, new event OnOAuth2ResponseError which allows to customize the HTTP response error.
 [+] : Improved JWT Server component, new event OnJWTResponseError which allows to customize the HTTP response error.
 [+] : Improved SignalR Client Component, added cookie authentication.
 [+] : Improved OpenSSL support. New property SSL_Options.Legacy to enable legacy provider for OpenSSL 3.+ version.
 [+] : Improved sgcIndy OpenSSL, new property LegacyProvider to load the legacy provider for backward compatibility.
 [+] : Improved sgcIndy OpenSSL, new method IdOpenSSLSetOSSLPath to set the path of the OSSL provider.
 [+] : Improved OpenAPI Parser handling classes with multiple inheritance.

 [*] : Fixed Bug sgcIDE Expert, the browser wasn't loaded automatically from the registry.
 [*] : Fixed Bug sgcIndy ALPN protocol on Server Components when running in Android.
 [*] : Fixed Bug setup when installing in a drive different from "C:\", file not found. 
 [*] : Fixed Bug Setup the package version was not showed. 
 [*] : Fixed Bug TsgcHTTPAWS_SQS_Client "SignatureDoesNotMatch error".
 [*] : Fixed Bug Internal Compiler Directive replaced {IFDEF WINDOWS} by {IFDEF MSWINDOWS}.
 [*] : Fixed Bug OpenAPI Client when a parameter in the path contained "/" character. 
 [*] : Fixed Bug OpenAPI Amazon S3 when uploading files using PutObject method. Added new method PutObjectAsStream to pass a stream as a parameter instead of a string.
 [*] : Fixed Bug OpenAPI Parser when the function returned a boolean, the internal function was defined as returning a string. 
 [*] : Fixed Bug OpenAPI Parser when the function didn't return any value.
 [*] : Fixed Bug OpenAPI Parser when implementing an Array Class of strings, there was an error in the DoRead method.
 [*] : Fixed Bug OpenAPI Parser in some cases the Array Class was not implemented properly.
 [*] : Fixed Bug Indy Server, when the property Specifications.RFC6455 was disabled, the TCP Connections where not accepted.
 [*] : Fixed Memory Leak using SChannel as IOHandler. (Thanks to Kenza for letting me know).
 [*] : Fixed Memory Leaks on Indy Server Component.





## 2024.7.0: 2024 August

 [+] : Improved OAuth2 Client, new grant type: auth2ResourceOwnerPassword which supports the Resource Owner Password Flow.
 [+] : Improved OpenAPI Parser, when using the Endpoint to take the method name, now adds the type of the method request (UsingGET, UsingPOST...) at the end of the name.
 [+] : Improved OpenAPI Client, added the property Count to the TsgcOpenAPIArray Class.
 [+] : Improved SChannel IOHandler, new property "UseLegacyCredentials" to force the use of the SCHANNEL_CRED.
 [+] : Improved Presence Protocol, when receiving a new Invitation, the client can set an error code and error text.
 [+] : Improved Presence Protocol, the client who sends the invitation now can know if the invitation has been accepted or not using the event OnChannelInvitationResponse.
 [+] : Improved MQTT Client on Delphi 7 and 2007, improved the speed reading big messages.
 [+] : Improved OpenSSL, the openSSL libraries for openSSL 3.3 have been compiled and are now available.
 [+] : Improved TsgcSocketConnection class, new property CreatedAt which stores the datetime when the connection is created.

 [*] : Fixed Bug OpenAI Assistant Demo, if the assistant was not created, an access violation was raised when sending a message (Thanks to Ad for letting me know).
 [*] : Fixed Bug OpenAPI Parser handling Boolean and Integer responses.
 [*] : Fixed Bug setup, if win32 was not selected, the design-time package was not compiled.
 [*] : Fixed Bug OpenAI Client, when calling the transcription method, an error was returned.
 [*] : Fixed Bug sgcIndy in the method X509_get_version when using openSSL 1.1.1 or 3.0.0.
 [*] : Fixed Bug sgcIndy "Error getting SSL method." 
 [*] : Fixed Bug SChannel, Range Check Error may be raised in the method TSSLInfo.Read.
 [*] : Fixed Bug SChannel, if the connection wasn't closed gracefully, the event OnDisconnect was not called.
 [*] : Fixed Bug HeartBeat, when the type was hbtOnlyIfNoMsgRcvInterval, the event OnBeforeHeartBeat was called even if the ping was not sent.
 [*] : Fixed Bug WebBrokerBridge for HTTP/2 and HTTPAPI, when the request was not found, the server didn't return a 404 error. (Thanks to Francesco for letting me know).
 [*] : Fixed Bug Compiling sgcWebSockets package with Lazarus on MacOS.
 [*] : Fixed some warnings while compiling.

 [/] : The event TsgcWSPClient_Presence.OnChannelInvitation has 2 new parameters aErrorCode and aErrorText. 



## 2024.6.0: 2024 June

 [+] : Improved OpenAI API, added support for Assistants (currently in Beta state).
 [+] : Improved OpenAI API, new demo showing how the new Assistants API work, it's located in the folder "Demos\15.AI\02.Applications\05.Assistant".
 [+] : Improved Setup, the parameters /username and /password have been added to set the user/password of the subscription.
 [+] : Improved OpenAPI Parser, the method name now can be taken from the Endpoint.
 [+] : Improved OpenAPI Parser, now can handle multiple responses when the successful response is not a class.
 [+] : Improved OpenAPI Parser handling Object Arrays.
 [+] : Improved WebPush Subscription object, new property RawText which contains the JSON string with subscription/unsubscription request.
 [+] : Improved TsgcHTTP1Client, new event OnSSLVerifyPeer to validate the SSL Certificates.
 [+] : Improved sgcIndy, added the latests X509 SSL Errors.

 [*] : Fixed Bug WriteAndWaitData method didn't exit if the connection was already disconnected and it was waiting till the end of the timeout.
 [*] : Fixed Bug AzureIoT Client, json encode error while sending the completion file upload in some cases.
 [*] : Fixed Bug GoogleCalendar Client, when creating a new event and the timeseparator was not ':', an error was returned.
 [*] : Fixed Bug AWS IoT client, the signatureV4 was not properly calculated when the local date was different from the UTC date.
 [*] : Fixed Bug sgcIndy when reading the properties notBefore and notAfter from the TIdX509 class.
 [*] : Fixed Bug Indy IOCP Server, when using plain TCP connection, the event OnTCPConnect was not called until some data was received.
 [*] : Fixed Bug TsgcHTTP1Client, the VerifyDepth was not set properly.
 [*] : Fixed Bug OpenAPI Client when using OAuth2 client component after calling a OpenAPI request.
 [*] : Fixed Bug OpenAPI Parser, error converting yaml file to json.
 [*] : Fixed Bug OpenAPI Microsoft, the OAuth2 url was not built properly in some cases. 
 [*] : Fixed Bug OpenAPI Amazon, when passing a TStream instead of a String as a body, there was an error calculating the signature.
 [*] : Fixed Bug using OpenSSL 3.0.0 on iOS.





## 2024.5.0: 2024 May

 [+] : Improved Binance API Client, new place order functions: PlaceMarketQuoteOrder, PlaceStopTrailingOrder, PlaceTakeProfitOrder, PlaceTakeProfitTrailingOrder and PlaceLimitMakerOrder.
 [+] : Improved Binance API Client, new method: GetPriceTickers to request multiple symbol prices in a single request.
 [+] : Improved Binance API REST Client, new property REST_API.BinanceOptions.RecvWindow, specify the number of milliseconds where the request must be processed or be rejected by the server (defaults to 5000).
 [+] : Improved OAuth2 Server, new property OAuth2Options.PKCE (Proof Key for Code Exchange) which is an extension of the OAuth 2.0 protocol that helps prevent code interception attacks.
 [+] : Improved OAuth2 Client, new value "oauth2CodePKCE" in the property OAuth2Options.GrantType, which enables PKCE on client side. This option is usually used in native and mobile applications.
 [+] : Improved OAuth2 Client, when using "oauth2CodePKCE", set the LocalServerOptions.Port = 0 to use a random port when starting the local server. 
 [+] : Improved OAuth2 Client Demo, the Dropbox OAuth2 Login now supports refresh tokens.
 [+] : Improved OAuth2 Client Demo, when using D11+ and the check TWebBrowser is checked, the demo uses the TEdgeBrowser instead of the TWebBrowser.
 [+] : Improved OpenAPI Client, 2 new events: OnUpload and OnDownload. These events allow to know the progress state of the current Upload or Download.
 [+] : Improved HeartBeat, new property HeartBeatType with 2 values: hbtAlways (works as before, the default) and hbtOnlyIfNoMsgRcvInterval (sends a ping only if no message has been received in the latest x seconds defined in the interval).
 [+] : Improved WebSocket Components, new Method WriteAndWaitData in TsgcWSConnection, sends a binary message and waits the response from the other peer.

 [*] : Fixed Bug Amazon AWS SDK Dynamodb, HTTP 404 not found.
 [*] : Fixed Bug Indy IOCP when trying to send a message and the connection was already closed.
 [*] : Fixed Bug Indy IOCP a potential deadlock while using the broadcast method.
 [*] : Fixed Bug Indy IOCP, socket error 10035 was not handled.





## 2024.4.0: 2024 April

 [+] : Improved Binance API Client, the convert endpoints have been added to the REST_API class.
 [+] : Added the property Options.Software to customize the Server HTTP Header value.
 [+] : New Demo showing how to use OpenAI to convert code from different languages, the demo is located in the folder "15.AI\02.Applications\04.CodeConverter".
 [+] : Improved TsgcOpenAIChatBot, new property HttpOptions.ReadTimeout to abort request if exceeds the timeout.
 [+] : Improved TsgcOpenAIChatBot, the methods ChatAsUser and ChatAsSystem have a new parameter to pass the previous history messages (Thanks to Andrea for the improvement). 
 [+] : Improved TsgcHTTPGoogleCloud_Calendar_Client, new method Clear, to switch between accounts.
 [+] : Improved HTTP.SYS Server, the ResponseInfo.ContentStream now can handle streams different from TStringStream (Thanks to Corbinian for the improvement).
 [+] : Improved OpenAPI Client, now supports sending a stream when calling POST or PUT requests.
 [+] : Improved OpenAPI Google SDK, there is a new demo showing how to upload/download a file to google drive, it's in the folder "Demos/01.google_drive". 
 [+] : Improved Amazon AWS IoT client, the Device MQTT Provisioning API methods have been implemented: CreateCertificateFromCsr, CreateKeysAndCertificate and RegisterThing.
 [+] : Improved Amazon AWS IoT Demo, the provisioning API methods now can be tested using the demo (Demos\10.IoT_Clients).
 [+] : Improved OAuth2 Client Demo, the Dropbox OAuth2 Login has been added (Demos\20.HTTP_Protocol\02.OAuth2_Authentication).

 [*] : Fixed Bug SignalRCore Client when decoding the MessagePack message.
 [*] : Fixed Bug TsgcHTTPOpenAIAzure_Options class, the properties were not published.
 [*] : Fixed Bug HTTP/2 Client when closing connection, a thread exception may be raised.
 [*] : Fixed Bug HTTP/2 Client, CustomHeaders property was using NameSeparator "=" instead of ":".
 [*] : Fixed Bug HTTP/2 decoding the StreamIdentifier.
 [*] : Fixed Bug UDP Client when reading the handshake. 
 [*] : Fixed Bug TsgcOpenAIChatBot, access violation while destroying component in the middle of a request (Thanks to Andrea for the fix).
 [*] : Fixed Bug MQTT Client, when receiving disconnect message (mqtt5 only), the OnMQTTDisconnect event was called twice.
 [*] : Fixed Bug Compiling for Lazarus in Linux environment, sgcWebSocket.dcr not found.
 [*] : Fixed Bug casting some internal variables with the wrong type.
 [*] : Fixed Bug Indy Server, the function to obtain the websocket sub-protocols supported hasn't a default value.

 [/] : Intraweb package that comes with old Delphi versions have been removed. Only Intraweb 15 is currently supported.





## 2024.3.0: 2024 March

 [+] : Updated the OpenSSL 1.1.1 libraries to the version 1.1.1w. This is the latest release for the Api 1.1.1.
 [+] : Updated the OpenSSL 3.0.0 libraries to the version 3.0.13.
 [+] : Updated the OpenSSL 3.1.0 libraries to the version 3.1.5. (These are currently the recommended openSSL libraries).
 [+] : Updated the OpenSSL 3.2.0 libraries to the version 3.2.1.
 [+] : Updated the Telegram libraries to the version 1.8.25. (Windows, Android, iOS, Linux64 and OSX).
 [+] : Improved the SignalRCore API Client, the protocol MessagePack is supported using an external library parser.
 [+] : Improved TsgcWebSocketLoadBalancerServer with the following new features:
 [+] :    - Support for the HTTP Protocol.
 [+] :    - New Events: OnLoadBalancerHTTPRequest and OnLoadBalancerHTTPResponse to fine-tune the HTTP requests.
 [+] : Improved the setup for trials and basic versions, now the Rad Studio Community Edition register automatically the pre-compiled packages.
 [+] : Improved the setup: there is a new option to enable Debug Mode, which stores in a text file the internal debug messages. Only use for Debug not for production.
 [+] : Improved the Telegram API Client, new method "EditTextMessage": Edits the text of a message.
 [+] : Improved Indy Server, new event "OnSSLVerifyPeer" to verify the client certificate is correct.

 [*] : Fixed Bug IOCP Indy Server, if there was an error while waiting for more data, the connection was not disconnected.
 [*] : Fixed Bug IOCP Indy Server, if the HeartBeat Timeout was exceeded, the connection was not disconnected.
 [*] : Fixed Bug IOCP Indy Server, if the message received was greater than the internal buffer, the connection was closed.
 [*] : Fixed Bug WebBrokerBridge indy file, it was using the indy unit instead of the custom indy.
 [*] : Fixed Bug WebBrokerBridge when compiling Rad Studio Versions older than 10.1.
 [*] : Fixed Bug sgcIndy Library, the event OnVerifyPeer was not called on Server components.
 [*] : Fixed Bug sgcIndy Library, when OnStatus events are handled, a potential access violation can be raised.
 [*] : Fixed Bug Disconnect exceptions were raised when writing binary data, but the RaiseDisconnectExceptions property was disabled.





## 2024.2.0: 2024 February

 [+] : New Component TsgcWSPClient_AMQP1, implements AMQP 1.0.0 protocol.
 [+] :    - Authentication: anonymous or SASLPlain
 [+] :    - Plain TCP / TLS.
 [+] :    - Create / Close Sessions.
 [+] :    - Create / Close Sender Links. 3 Send modes: settled, unsettled or mixed.
 [+] :    - Create / Close Receiver Links. 2 Read modes: automatic or manual.
 [+] :    - Await methods: CreateSession, CloseSession, CreateSenderLink, CreateReceiverLink, CloseLink, Close and SendMessage.
 [+] :    - Send Messages.
 [+] :    - Implemented Delivery States when receiving a message.
 [+] :    - HeartBeat.
 [+] :    - Idle TimeOut of connection.
 [+] :    - Connection & Session States.
 [+] :    - Close Connection method.
 [+] : New Demo AMQP1 which shows how works AMQP1 client, it's located in "02.WebSocket_Protocols\11.AMQP1_Client" folder.
 [+] : Improved Binance API, added 1 second interval to KLine intervals.
 [+] : Improved openSSL error message, now if there is any error loading the openSSL library, the API version is shown.
 [+] : Improved TsgcWebSocketHttpServer, new property HttpOptions.PoolOfThreads, allows to handle the HTTP Requests in a pool of threads.
 [+] : Improved TsgcWebsocketHttpServer, new event OnHTTP2BeforeAsyncRequest to fine-tune which requests are processed in the pool of threads or not.
 [+] : Improved the Installer, new Options: 
 [+] :    - sgcIndy Installed: (false by default) check this option when sgcIndy package is installed.
 [+] :    - sgcIndy Compatibility Mode: (false by default) check this option when sgcIndy package is compiled in Compatibility Mode (Package without Version Name, Copy DCPs to Lib folder...)
 [+] :    - Force the use of an OpenSSL API Version: Always use OpenSSL 1.1.1 or OpenSSL 3.0.0
 [+] :    - The /EXTRACT parameter now allows to customize the path where the files are extracted.

 [*] : Fixed Bug OpenAPI Client, when using OAuth2 and openSSL 3.0.0, the OAuth2 request was using openSSL 1.0.2. Now the API can be configured in the property Authentication.OAuth2.HttpClientOptions.
 [*] : Fixed Bug Disconnect exceptions were raised when writing the socket, but the RaiseDisconnectExceptions property was disabled.
 [*] : Fixed Bug when WatchDog.Monitor was enabled, the internal connection may not be destroyed properly.
 [*] : Fixed Bug OpenAPI Client, the OAuth2 internal component was not destroyed.
 [*] : Fixed Bug OpenAPI Client, the LogOptions property was not assigned properly.
 [*] : Fixed Bug when using sgcIndy and sgcWebSockets package.
 [*] : Fixed Bug removed the Critical Sections when reading SChannel Data because are not needed and slow down the write methods.
 [*] : Fixed Bug sgcWebSockets.js conflict with jquery with the event function. The Event function has been renamed to sgcCustomEvent.
 [*] : Fixed Bug Bybit V5 API, AsJSON function was not returning the JSON string, Signature was not properly encoded... (Thanks to Henk for the patch).




## 2024.1.0: 2024 January

 [+] : Added support for Lazarus 3.0
 [+] : Improved Bybit API Client, the client has been upgraded to V5 API.
 [+] : Improved Demo "05.Crypto\01.CryptoAPI", it has been updated to show how the new Bybit endpoints work.
 [+] : Improved Bitmex REST API Client, the method "GetInstrumentsActive" has been implemented.
 [+] : Improved OpenAPI Client, new property "EncodeBodyAsUTF8", if enabled, the JSON body is encoded as UTF8 (by default false).

 [*] : Fixed Bug when Compression and Fragmented messages were activated, the fragmented message was not compressed.
 [*] : Fixed Bug THttpServerRequest.ConnectionId was defined as Int64 instead of HTTP_CONNECTION_ID (this raised a Range Check Error on Win64).
 [*] : Fixed Bug HTTP/2 Indy Server, validating the stream identifiers must only be done in the headers or push-promise frames.
 [*] : Fixed Bug HTTP/2 Indy Server, more data frames were sent than the receive windows frames allowed.
 [*] : Fixed Bug Installing the Lazarus Package on Linux.
 [*] : Fixed Bug AMQP Client, when closing the connection, the internal channel thread was not destroyed.
 [*] : Fixed Bug Huobi Client, when notifyEvents = neNoSync, an exception EDecompressionError with message Zlib Error = -3 was raised.
 [*] : Fixed Bug Memory Leak when the Indy Server was using IOCP as IOHandler.
 [*] : Fixed Bug "F2084 Internal Error: C4963" compiling the package for CBuilder 2007.
 [*] : Fixed Bug Lazarus, the icons components where not displayed in the IDE.

 [/] : Removed the Bittrex client component.





## 2023.8.0: 2023 November

 [+] : Added support for Rad Studio 12 Athens.
 [+] : Updated the Indy version to the latest.
 [+] : New Client API: CEX PLUS: cryptocurrency exchange and trading platform. Implement WebSocket protocol for private and public channels.
 [+] : Improved Demo "05.Crypto\01.CryptoAPI" which shows how CEX Plus client API works.
 [+] : Improved Indy Servers, there is a new property "OpenSSL_Options.CurveList", which allows to set the curve list names for the openSSL library.
 [+] : Improved Azure IoT Client, now supports upload files using SAS and X509 Authentication.
 [+] : Improved Azure IoT Client, now supports Provisioning Device Client Register method.
 [+] : Improved the IoT Demo, now the Azure IoT Demo shows how to upload files to the Azure Servers.
 [+] : Improved Kucoin API Client, added the InnerTransfer function.
 [+] : Improved OpenAPI Amazon Glacier SDK, the header x-amz-sha256-tree-hash is calculated automatically if no value is set as a parameter.
 [+] : Improved OpenAPI Response, new property ResponseHeaders which contains the headers of the response.
 [+] : Improved HTTP Forwarding to handle the 302 response code.
 [+] : Improved HTTP Forwarding, new properties to customize the forward request: QueryParams, Host, Origin, LogFilename, NoCache and CustomHeaders.
 [+] : Improved Setup, now supports new command-line parameters: /extract /versions /platforms /ide.
 [+] : Improved IoT Clients, added new properties BoundIP, BoundPort, BoundPortMax and BoundPortMin to set the local address of the client.

 [*] : Fixed Bug SignalRCore Client, when sending a line break to the server the connection was closed.
 [*] : Fixed Bug SignalRCore Client, error sending an empty string argument.
 [*] : Fixed Bug OpenAPI Amazon AWS, fields defines as AllOf where defined as string by default.
 [*] : Fixed Bug OpenAPI Amazon AWS, an invalid signature was raised when calling some methods.
 [*] : Fixed Bug OAuth2 Server, when client-secret is not valid, the server returned the correct value in the error message (Thanks to Jan to let me know).
 [*] : Fixed Bug when using OnBeforeForwardHTTP event, the forward value was not cleared for every new request.
 [*] : Fixed Bug OpenAPI AWS SDK, the glacier interface doesn't include a required parameter. (Thanks to Chang to let me know).
 [*] : Fixed Bug Indy Server, when stopping the server an access violation may raise if the internal Scheduler is not assigned. (Thanks to Francesco to let me know).
 [*] : Fixed Bug Indy Server, when stopping the server, the internal SSL Handler was not destroyed.
 [*] : Fixed Bug Indy Server, authentication basic was failing to catch the authorization header. (Thanks to Francesco to let me know).
 [*] : Fixed Bug Server HTTP/2 protocol, ContentText was not preserving the correct charset. (Thanks to Francesco to let me know).
 [*] : Fixed Bug HTTP.SYS Server, when WriteTimeout was enabled, the internal queue may delete the wrong item in some cases.
 [*] : Fixed Bug SGC Server Protocol, the WriteData method was not working when using web-browser as a client.
 [*] : Fixed Bug Indy library, when using openSSL 1.1 SSL Status events where not fired.
 [*] : Fixed Bug Server Components when Extensions.PerMessage_Deflate was enabled and Options.FragmentedMessages = frgAll, the message was uncompressed 2 times.






## 2023.7.0: 2023 September

 [+] : Improved the Presence Server Protocol, new "Broadcast" method which allows to send a message to all connected clients using this protocol or to clients subscribed to a specific channel.
 [+] : Improved the Kraken API Client, added the Private User Funding methods of the REST API.
 [+] : Improved the Bitstamp API Client, added the WebSocket Private Methods.
 [+] : Improved the Bitstamp API Client, added the REST Public Methods.
 [+] : Improved the Bitstamp API Client, added the REST Private Methods: account balance, orders and Withdrawal.
 [+] : Updated the CryptoAPI Demo to show the new Bitstamp features.
 [+] : Improved the Kucoin API Client, added the Withdraw methods.
 [+] : Improved the OpenAI Client, now supports Microsoft Azure OpenAI Services (Completion and Chat Completion).
 [+] : Updated the OpenAI Demo showing how to use Azure OpenAI Services. It's located in the folder "15.AI\01.QuickStart\01.OpenAI".
 [+] : Improved the OpenAPI AWS Client, there is a new property AmazonOptions.SessionToken to set the token for temporary security credentials.  
 [+] : Improved the Huobi API Client, the private websocket methods are updated to version 2: SubscribeOrderUpdates, SubscribeTradeClearing and SubscribeAccountChange.
 [+] : Improved the Huobi API Client, there are 2 new methods: SubscribeBBO and SubscribeMarketByPrice.
 [+] : Improved the HTTP2 Client, there is a new property "HTTP2Options" which allows to configure how handle the fragmented data received.

 [*] : Fixed Bug HTTP/2 Server, Range Check Error.
 [*] : Fixed Bug HTTP/2 protocol, error decoding empty string.
 [*] : Fixed Bug HTTP/2 Client Demo, deleted all the golang test because the server is not active anymore.  
 [*] : Fixed Bug OpenAPI Amazon AWS, when the content-type was not "application/x-www-form-urlencoded; charset=utf-8", the message was not encoded properly.
 [*] : Fixed Bug OpenAPI Amazon AWS, the default url base was "http://" instead of "https://".
 [*] : Fixed Bug Identifier not found "Register" compiling Lazarus on Linux.
 [*] : Fixed Bug SChannel error "invalid pointer" when using Start/Stop threaded methods.
 [*] : Fixed Bug HTTP.SYS Server, protect the internal method to send the HTTP response when it's accessed from different threads for the same connection id.
 [*] : Fixed Bug HTTP.SYS Server, the property Options.WriteTimeout was not working, now it's implemented only when Asynchronous = False (the default option).
 [*] : Fixed Bug Kraken API Client, access violation when calling a method with and array of const as parameter from CBuilder.
 [*] : Fixed Bug SignalRCore Client, access violation when calling a method with and array of const as parameter from CBuilder.
 [*] : Fixed Bug OpenAPI, when enabling the compiler directive SGC_OPENAPI_JSON, the json object names were not preserving the case (Requires Rad Studio 10.4+).
 [+] : Fixed Bug Bybit API Client, the argument Quantity was defined as Integer instead of Extended (Thanks to Henk to let me know).

 [/] : Removed the Huobi API Private V1 Methods: GetAccounts, GetOrders, GetAccountsList, GetOrdersList and GetOrdersDetail.






## 2023.6.0: 2023 August

 [+] : New Pinecone API Client, it's a vector database which provides long-term memory for AI using embeddings from AI models.
 [+] : New Demo showing the main features of Pinecone API, it's located in the folder "15.AI\10.Vector_Database\01.Pinecone". 
 [+] : New TsgcAIDatabaseVectorFile, handles the OpenAI Embedding vectors using 2 files: one for vectors and another for the prompts. This component is for testing purposes, not for production. For production use any Vector Database like Pinecone.
 [+] : New TsgcAIDatabaseVectorPinecone, store and query the OpenAI Embedding vectors using the Pinecone API. 
 [+] : New Demo showing how to build a Questions & Answers application using custom knowledge data (stored in a pinecone database or in a text file) and OpenAI Chat API, it's located in the folder "15.AI\02.Applications\03.QA".
 [+] : Improved SignalR Component, now allows to send/receive binary data.
 [+] : New Demo showing how to login using a Google or Microsoft account in Mobile devices, the demo is located in the folder "Demos\20.HTTP_Protocol\09.OAuth2_Social\sgcOAuth2_Social_FMX".
 [+] : Fixed Demo OAuth2 Client using TWebBrowser on Windows 11, javascript not supported when trying to login using a google account.
 [+] : Improved ChatGPT Demo located in the folder "Demos\15.AI\01.QuickStart\04.ChatGPT". (Thanks to Dobrin for the improvements).

 [*] : Fixed Bug OpenAI Client, an exception was raised trying to read the vector embeddings response.
 [*] : Fixed Bug OpenAI Client, invalid JSON request "utf-8", the text was not encoded properly.
 [*] : Fixed Bug OAuth2 Server, the url parameters were not decoded.
 [*] : Fixed Bug FPC compiling SpeechToText components.
 [*] : Fixed Bug Telegram Client under Android, library cannot be loaded.
 [*] : Fixed Bug Telegram Client under Android 32, the following error was raised while compiling "component is not declared".
 [*] : Fixed Bug WebPush Demo, openSSL 3.0 was not set by default (Thanks to Ad to let me know).
 [*] : Fixed Bug sgcIdSSLOpenSSLHeaders_static compiling error on iOS when setting an openSSL API Version.
 [*] : Fixed Bug sgcIdSSLOpenSSLHeaders_static access violation error on iOS.




## 2023.5.0: 2023 June

 [+] : New TsgcAIOpenAIChatBot, is an OpenAI ChatBot Component, allowing to build a Voice Command ChatBot for Windows using OpenAI APIs and Text-To-Speech Providers like Google or Amazon.
 [+] : New TsgcAIOpenAITranslator, is an OpenAI Translator Component, allowing to build a Voice Command Translator Application for Windows using OpenAI APIs and Text-To-Speech Providers like Google or Amazon.
 [+] : New Component TsgcAudioRecorderMCI, allowing to record microphone audio and store into a wave file.
 [+] : New Component TsgcAudioPlayerMCI, allowing to play mp3 files.
 [+] : New Component TsgcTextToSpeechSystem, (for windows only) converts text to speech without the need of using an external mp3 file.
 [+] : New Component TsgcTextToSpeechGoogle: converts text to speech using any of the Google Cloud voices available.
 [+] : New Component TsgcTextToSpeechAmazon: converts text to speech using any of the Amazon AWS voices available.
 [+] : New Demos are located in the folder "15.AI\02.Applications".
 [+] : Improved SignalRCore Client, now supports Basic Authentication.

 [*] : Fixed Bug OpenAI Client, utf-8 characters were not encoded properly.
 [*] : Fixed Bug Indy EPOLL Server, Deadlock while stopping the server on Linux64.
 [*] : Fixed Bug Amazon AWS Client, signature error sending a POST request were the payload had UTF-8 chars.
 [*] : Fixed Bug OpenAPI Client, the TsgcOpenAPI_AdditionalProperties class was not destroyed automatically. (Thanks to Waldemar for the fix).
 [*] : Fixed Bug HTTP API Client, response to the POST requests were not UTF-8 encoded.
 [*] : Fixed Bug SignalRCore Client when authentication is enabled and try to reconnect an stackoverflow error is raised.
 [*] : Fixed Bug SignalRCore Demo, the client cannot connect to the default server.
 [*] : Fixed Bug EPOLL Server, the OnDisconnect event was not called in some cases (Thanks to Andrea for the fix).
 [*] : Fixed Bug IOCP Server, the OnDisconnect event was not called in some cases (Thanks to Andrea for the fix).
 [*] : Fixed Bug IOCP Server, using SSL connections, some internal events were not linked properly.
 [*] : Fixed Bug AMQP Client sending a message with a frame size greater than allowed.
 [*] : Fixed Bug AMQP Client receiving a message splitted in multiple frames, the message was received as multiple different messages, now is delivered as a single message.




## 2023.4.0: 2023 May

 [+] : New Server API Component TsgcWSAPIServer_WebPush, implements WebPush Protocol on Server Side, allowing to ask permission to the users, register the subscriptions, send notifications and more.
 [+] : New Client API Component TsgcWebPush_Client, implements WebPush Protocol on Client Side, allowing to send notifications to users via desktop and mobile web.
 [+] : New Demo showing the main features of WebPush Protocol, the sample can be found in the folder "20.HTTP_Protocol\11.WebPush_Notifications".
 [+] : Improved SignalRCore Client, new property SignalRCore.Authentication.TokenParam which allows to configure where pass the access_token, as a query parameter or as a header.
 [+] : Improved OpenAPI Parser, added support for AdditionalProperties.
 [+] : Improved OAuth2 Server, there is a new event "OnOAuth2Unauthorized" which is called when a request is not authorized and will be disconnected here you can configure which endpoints require OAuth2 Authentication and which not.
 [+] : Improved JWT Server, there is a new event "OnJWTUnauthorized" which is called when a request is not authorized and will be disconnected, here you can configure which endpoints require JWT Authentication and which not.

 [*] : Fixed Bug TsgcWebSocketServer, if a connection is closed with an error 10053 while is writing data, the thread freezes trying to closing the socket again.
 [*] : Fixed Bug TsgcWebSocketServer, if server receives an OPTIONS request while the Basic Authentication is enabled, the Server must not return a realm. Now the request is handled in the OnCommandOther event.
 [*] : Fixed Bug AMQP Protocol, if there was an exception inside the event OnAMQPBasicDeliver, the connection was closed.
 [*] : Fixed Bug OpenAPI Parser, deleted private/public sections not required.
 [*] : Fixed Bug RTCPeerConnection, EIntOverflow when converting an array of bytes to UInt64.
 [*] : Fixed Bug OpenAPI Parser fails to register the license if the installer were not used previously.
 [*] : Fixed Bug OpenAPI Client, the Objects and Property arrays were not destroyed. (Thanks to Waldemar for the fix).





## 2023.3.0: 2023 April

 [+] : Added Support for OpenAI API, which allows to interact with models like gpt-3.5-turbo, speech to text, translations, Image AI generation and much more.
 [+] : New Demos which show how to use the OpenAI API in the folder "15.AI".
 [+] : Improved TsgcWebSocketClient_WinHTTP, there is a new property "VerifyCertificate" to enable the Server Certificate Validation.
 [+] : Improved Amazon AWS SDK, the JSON classes now are created by default, to enable it, enable the compiler directive SGC_OPENAPI_JSON (Requires Rad Studio XE7+).
 [+] : New Demo showing how to stream video using the function IndyStreamFileVideo. The demo is located in the folder "04.WebSocket_Other_Samples\10.StreamVideo".
 [+] : Improved TsgcWebSocketClient, added new properties BoundIP, BoundPort, BoundPortMax and BoundPortMin to set the local address of the client.
 [+] : Improved OAuth2 Server Component, now supports Client Credentials authorization Grant Type.
 [+] : Improved OAuth2 Server Component, function AddToken now has a new parameter: Scope. 
 [+] : Improved OAuth2 Server Component, function AddToken now if the Token has expired but the RefreshToken exists, the token is added to the internal list and it's not discarded.
 [*] : Improved SignalR Client, new property SignalR.Authorization to allow Bearer Token Authentication.
 [*] : Improved WebSocket Server, Basic Authentication now allows to add Custom Headers.

 [*] : Fixed Bug TsgcWebSocketServer/TsgcWebSocketHTTPServer, some SSL Options were not properly initialised if SSL was enabled before the SSL options were set.
 [*] : Fixed Bug Datasnap Indy server, OnExceptionEvent was not found.
 [*] : Fixed Bug OpenAPI, path parameters may be wrong encoded in some cases.
 [*] : Fixed Bug OpenAPI Parser when the endpoint has more than 255 characters.
 [*] : Fixed Bug SChannel, the SSL Parameter parameter from CredentialsCallBack was not called properly. (Thanks to Stefan to let me know).
 [*] : Fixed Bug IOCP IOHandler, invalid pointer when destroying the internal connection.
 [*] : Fixed Bug Amazon AWS SDK, some POST methods were using a wrong ContentType.
 [*] : Fixed Bug Bybit API, the expire time was not set properly.
 [*] : Fixed Bug Range Check Error using SChannel as TLS Provider. 
 [*] : Fixed Bug OAuth2 Server processing the Token request, the server returns in some cases invalid_request.
 [*] : Fixed Bug Google Calendar Client, setting a timezone has no effect on the start/end event.
 [*] : Fixed Bug SignalRCore API, when calling the invoke method and passing an argument as an object, the json message was incorrect.

 [/] : TsgcWSAPI_FTX client API has been deleted.






## 2023.2.0: 2023 February

 [+] : Added Support for Rad Studio 11.3.
 [+] : New OpenAPI Pascal Parser, imports any openAPI 3.0, Swagger 1.0 or 2.0 specification and creates a pascal interface file.
 [+] : Improved HTTP.SYS Server, new event OnTCPConnect, is called AFTER the TCP connection and BEFORE Websocket handshake or HTTP read request.
 [+] : Improved WebSocket Servers (Indy and HTTP.SYS), New Property "Groups" which provides methods for broadcasting messages to specified subsets of connected clients.
 [+] : New Demo "01.WebSocket_Quick_Start\12.Groups" showing how to use the Groups to broadcast messages to specific client connections. 
 [+] : New Demo "01.WebSocket_Quick_Start\14.Groups_Users" showing how to use the Groups combined with Custom Data Objects for identifying connection clients.
 [+] : Improved TsgcHTTP1Client, new method "GetSSE" to handle SSE requests, the messages are dispatched in the event "OnSSEMessages".
 [+] : New Demo "20.HTTP_Protocol\10.SSE_Client" showing how the SSE client works: connects to the HTTP server and receives the SSE event messages.

 [*] : Fixed Bug MQTT Demo, publish method took the channel name from the subscribing channel textbox instead of the publishing channel textbox. 
 [*] : Fixed Bug compiling sgcWebSockets package for RAD Studio 2007: "HRESULT is not a member of sgcwebsocket_httpapi".
 [*] : Fixed Bug when connection was closed pending asynchronous messages were not removed from internal queue. (Thanks to Martijn to let me know).
 [*] : Fixed Bug Binance, added millisecond resolution to the timestamp signature field. (Thanks to Gorazd to let me know).
 [*] : Fixed Bug Kraken handling prices with more than 4 decimals.
 [*] : Fixed Bug Binance Futures connecting to user data stream.
 [*] : Fixed Bug OpenAPI Parser, the object arrays were not handled when reading a response with arrays.
 [*] : Fixed Bug OpenAPI Parser, in some cases, the objects were defined as strings instead of classes.
 [*] : Fixed Bug OpenAPI SDK, parameters were not properly encoded.
 [*] : Fixed Bug OpenAPI Parser, now integers are parsed as Int64.





## 2023.1.0: 2023 January

 [+] : Updated Telegram libraries to version 1.8.9.
 [+] : Improved Telegram Client, when there is an error while loading the library on MacOS, now the error message with the reason is caught.
 [+] : Improved Indy Server, new property SSLOptions.OpenSSL_Options.CipherList to customize the Cipher List.

 [*] : Fixed Bug IOCP IOHandler and SSL, if there was an error while writing data, the connection was not closed.
 [*] : Fixed Bug compiling sgcWebSockets 2022.10.0 for Lazarus on Linux.
 [*] : Fixed Bug Indy server, error: list index out of bounds while handling heartbeat timeout.
 [*] : Fixed Bug Installing Lazarus Trial package.
 [*] : Fixed Bug Telegram Client, error loading library on OSX64.
 [*] : Fixed Bug WebSocket Server when Basic Authorization was enabled, when a request has not authorization or it was wrong, the server disconnected the connection without asking the realm.
 [*] : Fixed Bug compiling sgcWebSockets package for CBuilder 2007.
 [*] : Fixed Bug compiling IOS64, 2 functions were not properly defined and the build failed. (Thanks to Kick to let me know).
 [*] : Fixed Bug compiler directives SGC_OPENSSL_API_1_1 and SGC_OPENSSL_API_3_0, the TLSOptions and SSLOptions of Components changed the API Version when these compiler directives were defined.




## 2022.10.0: 2022 December

 [+] : New Client API: Bybit: cryptocurrency exchange and trading platform. Implement WebSocket protocol for: Spot, Inverse Perpetual, USDT Perpetual and Inverse Futures.
 [+] : Improved Demo "05.Crypto\01.CryptoAPI" which shows how Bybit client API works.
 [+] : Improved WhatsApp API to version 15.0.
 [+] : Improved WhatsApp API, new method "UploadMedia" to upload images, documents... to whatsapp servers.
 [+] : Improved WhatsApp API, template parameters like image, document... now have a new property "id" where you can set the id of the previously uploaded media file (instead of using a link).
 [+] : Improved OAuth2 Client on Linux, now supports opening urls in web-browser when requires client interaction for authentication.
 [+] : Improved sgcWebSockets setup, a new option to install Rad Studio package (Delphi and CBuilder).
 [+] : Improved RTCMultiConnection API, updated to the latest socket.io version.
 [+] : Improved WebRTC Server API, new property "CloseSessionOnHangup", if disabled, when a peer close a session, the other peer is not disconnected (by default is true).

 [*] : Fixed Bug compiling sgcWebSockets 2022.9.0 for Lazarus.
 [*] : Fixed Bug SChannel Win64, access violation while starting ssl connection. (Thanks to Anders to let me know).
 [*] : Fixed Bug HTTP.SYS Server when Asynchronous mode is enabled, the event OnDisconnect was fired twice.
 [*] : Fixed Bug CBuilder Setup, when uninstalling the CBuilder paths were not removed.
 [*] : Fixed Bug RTCMultiConnection Screen Sharing Demo, the connection may fail in some cases.
 [*] : Fixed Bug IOCP IOHandler, on heartbeat timeout exceeded, the connection was not closed.




## 2022.9.0: 2022 November

 [+] : Added support for EPOLL on Linux Indy Servers (Websocket and HTTPs Servers). The property IOHandlerOptions.IOHandlerType has a new value called iohEPOLL. 
 [+] : New Property "IOHandlerOptions.EPOLL" on Indy Servers, to configure the EPOLL IOHandler Server properties.
 [+] : New Demo which shows how the Indy EPOLL Server works in the folder "03.WebSocket_High_Performance_Server\03.Indy_EPOLL_Server".
 [+] : Improved IOCP on Windows Indy Servers (WebSocket and HTTPs Servers). The IOHandler has been rewritten from scratch and performance has been optimized.
 [+] : Improved Google OpenAPI Client:
       - New Property ServiceAccountOptions allowing to use some APIs like Calendar API with Domain-Wide Delegation.
       - New method ClearOAuth2Token to force re-authentication against Google Servers when using OAuth2 as Authentication.
       - If the server returns 401 error, now the internal OAuth2 tokens are cleared, so next time the client will request a new authentication.
 [+] : Improved TsgcHTTPGoogleCloud_Calendar_Client now supports Authentication using Service Accounts with Domain-Wide Delegation.	   
 [+] : Improved SChannel IOHandler, now implements SCH_CREDENTIALS instead of the deprecated SCHANNEL_CRED.


 [*] : Fixed Bug Google Calendar Client, when the Token was refreshed, the requests sent the old and the new token.
 [*] : Fixed TsgcWSPServer_sgc, an access violation may be raised when accessing an internal queue in some cases.
 [*] : Fixed Bug JWT, access violation on ES Algorithm when using openSSL 1.1 or 3.0.
 [*] : Fixed Bug compiling iOS64, sgcIdSSLOpenSSLHeaders_static.pas(1284): E2035 Not enough actual parameters.
 [*] : Fixed Bug sgcWebSockets configuration package for Linux on Delphi 10.3 and 11.0.




## 2022.8.0: 2022 October

 [+] : Added support for new iOS Simulator for ARM64 (Rad Studio 11.2).
 [+] : Added support for DTLS over UDP (Server and Client components).
 [+] : New Component TsgcRTCPeerConnection, allows to connect and exchange data between 2 remote peers (P2P if available). 
 [+] : New Demo "35.P2P\05.RTCPeerConnection" that shows how connect 2 remote peers.
 [+] : Improved Coinbase Pro API, the following Withdraw methods have been updated to latest: WithdrawalCoinbase, WithdrawalCrypto and GetWithdrawalFeeEstimate.
 [+] : Improved Server, there is a new property SSLOptions.VerifyCertificate_Options with 2 new options: FailIfNoCertificate (if the client doesn't provide a certificate the connection is closed) and VerifyClientOnce.

 [*] : Fixed Bug TURN Server, STUN binding requests were not relayed to the correct ip address.
 [*] : Fixed Bug OpenAPI Parser, when a class inherited the fields from another, the fields were created on both (master and child class).
 [*] : Fixed Bug TsgcWebSocketClient, when watchdog use Start method to reconnect it may occur in the middle of another reconnection, creating more than 1 thread trying to reconnect.
 [*] : Fixed Bug using HTTPUploadFiles, when receiving a filename with extended UTF8 characters, the filename was not decoded properly.
 [*] : Fixed Bug OpenAPI Amazon AWS error "SignatureDoesNotMatch" when the signature was not ordering the headers properly.
 [*] : Fixed Bug HTTP.SYS Server, the ContentText Response was not encoded to UTF-8 when the ContentType charset was set to utf-8.
 [*] : Fixed Bug Component Palette, in some cases the components couldn't be selected from multiple personalities. (Thanks to Laurent to let me know). 



## 2022.7.0: 2022 September

 [+] : New Client Component TsgcWSAPI_XTB. FX and CFD trading, providing access to over +2000 financial markets.
 [+] : New XTB demo showing the main features of crypto api. It's in the folder "05.Crypto\01.CryptoAPI" 
 [+] : Improved Binance Client, now supports Wallet API: Withdraw requests, universal transfers, deposit history and more.
 [+] : Updated Binance demo to show the use of the Wallet API. It's in the folder "05.Crypto\01.CryptoAPI" 
 [+] : Improved AMQP Client, now the following methods: DeclareExchange, DeclareQueue, BindQueue, UnBindQueue and Consume have a new parameter to pass custom arguments.
 [+] : Improved WhatsApp API, added new methods to Send Local Files as a Message: SendFileDocument, SendFileImage, SendFileVideo...
 [+] : Improved WhatsApp API, new event OnBeforeSendMessage, this event is called before the message is sent to WhatsApp and allows to read/update the message in JSON format.
 [+] : Improved WhatsApp API, new method DownloadMedia to download media given an object id.
 [+] : Improved OpenAPI client, now supports setting a bearer token directly in the request.
 [+] : Improved TURN Server, new events: OnTURNBeforeRelayIndication and OnTURNBeforeRelayChannelData allowing to capture the audio/video data when using a relayed address.

 [*] : Fixed Setup error, when building CBuilder Package for Android the following error can stop the building process "F1026 File not found: 'ldandroid.exe'". 
 [*] : Fixed Bug FXCM, the FXCM Server was updated and the client can not authorize against the server.
 [*] : Fixed Bug Setup installing CBuilder 11.4+ and Win64 (Fatal: Error detected (WRI237).
 [*] : Fixed Setup Error, msbuild fail when dcc command line compiler greater than 32000 Characters.
 [*] : Fixed Bug HTTP.SYS Server, when Basic Authentication was wrong, access violation was raised after sending the REALM.
 [*] : Fixed Bug HTTP.SYS Server, the property THttpServerRequest.Headers doesn't include all headers.
 [*] : Fixed Bug List Index out of Bounds accessing to count property of internal queue.
 [*] : Fixed Bug deleting websocket ping from internal queue after receiving a pong.
 [*] : Fixed Bug calling RegisterProtocol as string several times with the same protocol name, the events are duplicated.





## 2022.6.0: 2022 July

 [+] : New Client Component TsgcWSAPI_OKX. OKX, formerly known as OKEx, is one of the largest crypto spot and derivatives trading exchanges.
 [+] : New OKX demo showing the main features of crypto api. It's in the folder "05.Crypto\01.CryptoAPI"
 [+] : New Client Component TsgcICEClient, implements ICE RFC 8445 protocol.
 [+] : New ICE demo showing how ICE client works (requires websocket server for signaling and STUN/TURN server).
 [+] : Improved WhatsApp API, added the Location to the message received.

 [*] : Fixed Bug sending Big Files through HTTP Protocol, out of memory error.
 [*] : Fixed Bug WhatsApp API, sending the location has a bug in the address name node. (Thanks to Dirk to let me know).
 [*] : Fixed Bug Amazon SQS Component, DeleteMessage was not working.
 [*] : Fixed Bug MQTT Client, Range Check Error while reading a published message.
 [*] : Fixed Bug Installer sometimes return the error "The remote server is not available, please check your internet connection" when there was a valid connection.
 [*] : Fixed Bug when HTTPUploadFiles was enabled, the file received has 2 extra bytes. (Thanks to Allen to let me know).
 [*] : Fixed MemoryLeak when HTTPUploadFiles was enabled.
 [*] : Fixed Bug Socket.IO, the path was set after the /socket.io

 [/] : The Demo "01.WebSocket_Quick_Start\02.WebSocket_Clients_APIs" has been splitted in 2: WebSocket and Crypto APIs, now the Crypto APIs are in the folder "05.Crypto\01.CryptoAPI"




## 2022.5.0: 2022 June

 [+] : New WhatsApp Client, allows to send and receive messages, documents, images... using Whatsapp Cloud API.
 [+] : New WhatsApp Demo, shows how works the WhatsApp Cloud API: send messages, receive notifications...
 [+] : New OpenAPI Client Amazon AWS SDK. Allows to make HTTP Requests to Amazon AWS SDK Services.
 [+] : New OpenAPI Client Google Cloud APIs. Allows to make HTTP Requests to Google Cloud REST Services. 
 [+] : New OpenAPI Client Microsoft/Azure APIs. Allows to make HTTP Requests to Microsoft And Azure REST Services.
 [+] : New OAuth2 Authentication Client for Google, allows users login with Google Credentials and retrieve the profile info.
 [+] : New OAuth2 Authentication Client for Microsoft Azure, allows users login with Microsoft Credentials and retrieve the profile info.
 [+] : New Demo showing the OAuth2 Authentication for Google and Microsoft in the folder "20.HTTP_Protocol\09.OAuth2_Social"
 [+] : Improved RTCMultiConnection Demo, Added Video-Conferencing sample.

 [*] : Fixed Bug HTTP/2 Client, memory leak when the client was destroyed just after receive an HTTP Request.
 [*] : Fixed Bug Numeric Overflow connecting to a MQTT 5.0 server.
 [*] : Fixed Bug RangeCheck error.
 [*] : Fixed Memory Leak TsgcUDPCLient and TsgcUDPServer, the property TLSOptions was not destroyed.
 [*] : Fixed Memory Leak TsgcSTUNClient, internal TCP client was not destroyed.
 [*] : Fixed Bug Amazon IoT MQTT Client, error connecting when using SignatureV4. (Thanks to Jurgen to let me know).
 [*] : Fixed Bug connecting to Socket.IO 4 Server.




## 2022.4.0: 2022 April

 [+] : ZLib has been updated to 1.2.12, includes the latest security fix (*only Enterprise Edition).
 [+] : ZLib now can use a dll instead of using static linking using the conditional define "SGC_DYNAMICLOAD_ZLIB" (*only Enterprise Edition with source code).
 [+] : New Event on Server components "OnHTTPUploadReadInput" to read the Input Values when a file is received.
 [+] : Improved STOMP RabbitMQT Client, the Publish methods now have a new parameter "Headers", where optional custom headers can be sent to the RabbitMQ server. 
 [+] : Improved OAuth2 Client Demo, now shows how use a TWebBrowser instead of WebBrowser for Azure AD.
 [+] : Improved Pusher Client, now supports Cache Channels.
 [+] : Updated Lazarus to 2.2.0

 [*] : Fixed Bug installer, if the username/password contains some special characters, an empty error was returned and the install cannot continue.
 [*] : Fixed Bug installer (for registered users), when trying to install in a network drive raises the error "path does not exists". 
 [*] : Fixed Bug Enterprise Basic Edition, compiling datasnap server raise the error: sgcIndy.inc file not found.
 [*] : Fixed Bug WebBroker Enterprise HTTPAPI, compiling error: Undeclared identifier CustomHeader.
 [*] : Fixed Bug Trial after installing the library, unknown proc error was returned.
 [*] : Fixed Bug DataSnap and HTTP.SYS when processing a response, an invalid pointer was raised while trying to free an already destroyed stream.
 [*] : Removed some unused references from Delphi 7 package.
 [*] : Fixed Bug STOMP Client, an internal object was not freed when the client was destroyed. (Thanks to Preben to let me know).
 [*] : Fixed Bug Binance Client, the method "UnSubscribeKLine" didn't stop receiving KLine updates.
 [*] : Fixed Bug DataSnap HTTP/2 Server, "There is no overloaded version of 'DoHTTP2Response' that can be called with these arguments".
 [*] : Fixed Bug DataSnap HTTP/2 Server, if the server received an HTTP/1 requests (instead of HTTP/2) the datasnap method was not processed properly.
 [*] : Fixed Bug OAuth2 Client, after receiving a successful Access Token, sometimes a favicon request was processed as invalid.
 [*] : Fixed Bug using openSSL 3.0, access violation calling a deprecated method when an internal error occurs.



## 2022.3.0: 2022 March

 [+] : New sgcWebSockets Package Installer, install and register sgcWebSockets Library.
 [+] : New IDE AddOn, allows to automatically login from Rad Studio IDE and access to private downloads, support, forum... and more.
 [+] : New Component OAuth2 Server Provider, allows to integrate external OAuth2 Providers like Azure AD, Google, Facebook... so the user can login using Azure Credentials to your Server.
 [+] : New Component TsgcWSAPI_Kucoin, Kucoin client component to Trade and Get updates of Stock markets. Supports: 
       - WebSocket Public and Private Channels.
	   - REST Public and Private Endpoints.
 [+] : New Component TsgcWSAPI_Kucoin_Futures, Kucoin client component to Trade and Get updates of Futures markets. Supports: 
       - WebSocket Public and Private Channels.
	   - REST Public and Private Endpoints.	   
 [+] : Improved Telegram API, updated to 1.8.1 version.
 [+] : Improved Telegram API, added support for Sponsored Messages. New method "getChatSponsoredMessage" to retrieve sponsored messages, the messages will be notified "OnMessageSponsored" event.
 [+] : Improved Telegram API, from 1.7.0 the sender_user_id is zero, there are 2 new objects to read the sender of the message: SenderChat and SenderUser. 
 [+] : Improved Telegram API, new method SendInvoiceMessage allows bots to send invoice messages.
 [+] : Improved IoT Clients (Amazon and Azure), new method Disconnect to close and wait till the connection is closed.
 [+] : Improved FTX Client, now supports FTX.us broker.

 [*] : Fixed Bug HTTP/2 Client, running on Linux64 the error "ALPN h2 is not supported" was raised.
 [*] : Fixed Compiling runtime packages for Linux64. (Thanks to Kick to let me know).
 [*] : Fixed Azure IoT Client, range check error when decoding Secret Key.
 [*] : Fixed Bug IoT Client, if the client is destroyed while there is a connection active, it may lock the thread till the connection is closed automatically.
 [*] : Fixed Bug WebSocketClient, when DEBUG was enabled, the thread which started the connection was renamed instead of the internal thread. (Thanks to Ulrik to let me know).
 [*] : Fixed Bug WAMP Client, if several messages were received/sent the message may become corrupted in some cases.
 [*] : Fixed Bug Sending HTTP/2 Response from server, the content was empty.




## 2022.2.0: 2022 February

 [+] : Improved Amazon AWS IoT Client, SignatureV4 has a new property "OpenSSL_Options" which allows to configure the openSSL library options.
 [+] : Improved HTTP.SYS server, now THttpServerResponse has a new propery "FileName" where you can set the full path of the file to be sent as a response.
 [+] : Improved FXCM API Client, there is a new property "Demo" which allows to use a Demo account to test the FXCM Broker.
 [+] : Improved TsgcWSWConnection.Close method, now if the Code is below zero, the close packet doesn't include the reason for closing.

 [*] : Fixed Bug compiling Lazarus under Linux.
 [*] : Fixed Bug GetDateTimeUnix on Lazarus, the DateTime was always processed as Local Time. (Thanks to Henk to let me know).
 [*] : Fixed Bug Binance Client, if BinanceUS was selected, the REST API object was calling to Binance.com server.
 [*] : Fixed Bug Binance, Bitmex, Bittrex, Cex and Bitstamp clients, the function to obtain a valid Timestamp, was pointing to an old function.
 [*] : Fixed Bug FTX Client, the Boolean values were passed as quoted strings.
 [*] : Fixed Bug FXCM API, the client cannot connect to FXCM Servers.
 [*] : Fixed Bug SignalR Client, the value of Url returned in the negotiation it wasn't save properly.
 [*] : Fixed Bug Reading HTTP/2 StreamDependency as 31 bit value.
 [*] : Fixed Bug Handling HTTP/2 Protocol under Linux64 (Delphi).
 [*] : Fixed Bug Handling HTTP/2 Protocol under Linux (Lazarus).
 [*] : Fixed Bug some compiler defines for OpenSSL 1.1 and 3.0 were not defined properly.
 [*] : Fixed Bug HTTP/2 and Firefox, an internal error closed the connection.
 [*] : Fixed Bug TsgcWebSocketClient, after calling TsgcWSConnection.Close, the OnDisconnect event was not fired.

 [/] : Deleted FXCM properties: Host, Port and TLS.



## 2022.1.0: 2022 January

 [+] : New Component TsgcWSPClient_AMQP, implements AMQP 0.9.1 protocol.
 [+] : New Demo AMQP which shows how works AMQP client, it's located in "02.WebSocket_Protocols\10.AMQP_Client" folder.
 [+] : Improved BITMEX API Client, REST API is now supported: place orders, Cancel orders, Amend Orders, Close Position... and more.
 [+] : Improved BITMEX API Client, WebSocket API now can connect to TestNet.
 [+] : Improved BITMEX Demo, has been updated to reflex the new features: REST API, TestNet... is in the folder "01.WebSocket_Quick_Start\02.WebSocket_Clients_APIs".
 [+] : Improved WebRTC Protocol, new property "WebRTC.IceServers" which allows to configure custom ICE Servers.
 [+] : Improved Pusher Client, new OnPusherAuthentication event to allow implement custom authentication on private and presence channels.
 [+] : Improved Telegram Client, Sending a message has a new parameter to send buttons requesting the phone number, location... (for bots only).
 [+] : Updated Telegram Libraries to 1.7.9 version to fix the error UPDATE_APP_TO_LOGIN when the user login using a phone.
 [+] : Improved Binance Client, now supports Binance.US API (WebSocket and REST APIs).
 [+] : Improved Binance Client, new property "Binance.ListenKeyOnDisconnect" allows to define if the ListenKey is deleted when client disconnects or not.
 [+] : Improved Binance Client, new property "Binance.UseCombinedStreams" if enabled, events are wrapped as follows: {"stream":"<streamName>","data":<rawPayload>}.
 [+] : Improved SChannel, now works on Delphi 7, 2007 and 2009 (*Enterprise edition only).
 [+] : Improved PDF Documentation: support for syntax highlighting, image compression, automatic hyphenation, embeded fonts and more.
 [+] : Improved HTML Help Documentation, now supports syntax highlighting.

 [*] : Fixed Bug compiling CBuilder 2010, PVOID symbol definition conflict.
 [*] : Fixed Bug using JWT CLient and openSSL 1.1 libraries.
 [*] : Fixed Bug APIs (like Binance, FTX...) always make use of openSSL 1.0.2 instead of taking the configuration of TsgcWebSocketClient.
 [*] : Fixed Bug WebRTC Protocol, when a user disconnect from a channel other channels may be disconnected too.
 [*] : Fixed Bug MQTT Client when writing/reading had a high load of messages, the message may become corrupted in some cases.
 [*] : Fixed Bug SignalR Client, there was an error reconnecting when watchdog was enabled and the client cannot recover the connection automatically.
 [*] : Fixed Bug Binance and Kraken Clients, if the event OnHTTPException wasn't handled, the exceptions weren't shown to the user.
 [*] : Fixed Bug SChannel wasn't working under Lazarus.
 [*] : Fixed Bug WebSocket Server sending fragmented messages when compression was enabled.
 [*] : Fixed Bug when PerMessage_Deflate was enabled, while reading a compressed message, Z_BUF_ERROR may close the connection.
 [*] : Fixed Bug TsgcWebSocketClient, OnDisconnect event may not be called in some special cases.
 [*] : Fixed Bug WebSocket Server, if the property Active was set to True, when the server was already started, an access violation was raised.





## 4.5.4: 2021 November

 [+] : Improved TLSOptions.Version property, now if the value is tlsUndefined (the default), the client will try to negotiate all possible TLS versions (from TLS 1.3 to TLS 1.0), before this change the TLS 1.0 was selected.
 [+] : Improved Amazon AWS IoT Client, new property SignatureV4.SessionToken which must be filled when using temporarity security credentials.
 [+] : Improved HTTPUploadFiles, now there are 2 new events: OnHTTPUploadBeforeSaveFile and OnHTTPUploadAfterSaveFile, allowing to know/modify the name of the file received.
 [+] : Improved openSSL configuration, if openSSL_Options.LibPath = oslpCustomPath then will set the openSSL libraries location to the value of OpenSSL_Options.LibPathCustom (Thanks to Matteo for the suggestion).
 [+] : Improved openSSL configuration, new property UnixSymLinks allows to disable the loading of SymLinks under Unix. Fixes the error "Clients should not load the unversioned libcrypto dylib as it does not have a stable ABI." under MacOS Monterey.
 [+] : Improved openSSL error message "cannot load opensssl", now shows the path, methods not available and version. It's available only on Enterprise Edition.
 [+] : Improved Socket.IO API, added support for latest API 4.
 [+] : Added Support for Cryptorobotics Send Signal method.

 [*] : Fixed Bug Indy Servers, in some cases half-disconnected http connections may make use of the full cpu. (Thanks to Moacir to let me know).
 [*] : Fixed Bug when PerMessage_Deflate, handling a Z_BUF_ERROR message.
 [*] : Fixed Bug when PerMessage_Deflate, if an empty string or memory stream was sent, an error was raised.
 [*] : Fixed Bug when PerMessage_Deflate, if there was an internal error while inflating or deflating, the error message was not passed to the exception.
 [*] : Fixed Bug when PerMessage_Deflate, when inflating a stream, if the buffer wasn't big enough, the stream wasn't fully compressed.
 [*] : Fixed Bug TsgcWebSocketClient using plain TCP Protocol and TLS 1.3, the connection locks the thread during some seconds.
 [*] : Fixed Bug when the property HTTPUploadFiles.RemoveBoundaries was enabled, the filename were not extracted on older Delphi versions.
 [*] : Fixed Bug when the property HTTPUploadFiles.RemoveBoundaries was enabled, if the filename had spaces, the filename was not extracted completely.
 [*] : Fixed Bug when compiling TsgcWebSocketClient_WinHTTP under CBuilder, Ambiguity error with Wininet unit (HINTERNET, INTERNET_PORT).
 [*] : Fixed Bug MQTT Client read/write VarInteger values.
 [*] : Fixed Bug MQTT Client when publishing a message with PublishProperties, always sent the property TopicAlias = 1.

 [/] : The property TsgcWebSocketClient.Active now returns if the internal connection is Assigned or not. Before that, it called the Connected function of TCP Client.




## 4.5.3: 2021 October

 [+] : Added support for OpenSSL 3.0.0
 [+] : New Component TsgcWSAPIServer_RTCMultiConnection, server implementation of RTCMultiConnection project based on WebRTC which allows: MultiVideoConferences, Screen Sharing and Video Broadcasting.
 [+] : New Demo RTCMultiConnection in "30.WebRTC_Protocol\04.RTCMultiConnection" which shows how to use the TsgcWSAPIServer_RTCMultiConnection component.
 [+] : Improved Pusher Client, the REST methods: Trigger Events, Get Channels and Get Users have been implemented.
 [+] : Improved FTX Client, new methods for placing trigger orders: PlaceTriggerStopOrder, PlaceTriggerTrailingStopOrder and PlaceTriggerTakeProfitOrder.
 [+] : Improved Binance Client, new property UserStream, allows to disable the subscription to the websocket user stream.
 [+] : Improved Binance Client, if there is any error while doing an HTTP Request to the UserStream, the exception message now includes the Payload message.
 [+] : Improved TIdCookie, new property SameSite to prevent the cookie being blocked. The default value is "Lax".

 [*] : Fixed Bug Binance Futures API, when calling ChangeMarginType returns the error "mandatory parameter timestamp was not sent".
 [*] : Fixed Bug Binance Client when TsgcWebSocketClient.IOHandler = iohSChannel the HTTP ListenKey Requests were using openSSL libraries instead of SChannel.
 [*] : Fixed Bug TURN Server, when server receive a new ICE binding request, the packet wasn't processed properly.
 [*] : Fixed Warnings compiling for Delphi 7 (Thanks to Marc to let me know).
 [*] : Fixed Bug Loading OpenSSL 1.0.2 libraries on Old Delphi versions, the Windows libraries have been updated.
 [*] : Removed websocket.org from demos, service is no longer available.
 [*] : Fixed Bug OAuth2 Client, the Scope parameters was double encoding when using Indy version included with Rad Studio 10.3 or previous versions.
 [*] : Fixed Bug SChannel, memory was modified after the object was destroyed. (Thanks to Anders to let me know).
 [*] : Fixed some SChannel Memory Leaks when destroying TsgcWebSocketClient.
 [*] : Fixed Bug installing sgcWebSockets package in Rad Studio (Delphi and CBuilder), components were only visible in Delphi Personality.
 [*] : Fixed Bug SocketIO Client, if TsgcWebSocketClient was configured with a proxy, the HTTP request to get the session was executed without using the proxy.
 [*] : Fixed Bug TsgcWebSocketClient, Thread-lock when openSSL = TLS1.3 and immediately after setting Active := True, the property Active was evaluated.



## 4.5.2: 2021 September

 [+] : Added support for Rad Studio 11 Alexandria.
 [+] : New Component TsgcTURNServer, implements the STUN/TURN Server Protocol.
 [+] : New Component TsgcTURNClient, implements the STUN/TURN Client Protocol.
 [+] : New Demo which shows how use TURN Server and Client, is located in folder "35.P2P\03.TURN".
 [+] : New Component TsgcWSAPI_ThreeCommas, it's a crypto trading bot.
 [+] : Improved TsgcHTTP_Cryptohopper:
       - New methods: SendSignal, SendTestSignal and GetSignalStats.
       - The class TsgcHTTPCTHopper has a new field "Strategy" which allows to set a strategy for the hopper.
 [+] : New Property "ConnectHeaders" in STOMP Broker Clients, allows to send custom Headers when client connects to server.
 [+] : New Demo which shows how use DevExtreme DataGrid and sgcWebSockets library, the demo is located in folder "04.WebSocket_Other_Samples\07.DevExtreme_Grid"

 [*] : Fixed Bug TsgcWebSocketClient when running in a secondary thread and using openSSL libraries.
 [*] : Fixed Memory Leak on TsgcWebSocketHTTPServer when sending the HTTP response as a Binary object.
 [*] : Fixed Memory Leak using IOCP on Indy WebSocket Server. (Thanks to Anders to let me know).
 [*] : Fixed Bug MQTT Protocol, from Delphi 7 to 2009, the messages were not sent UTF8 encoded.
 [*] : Fixed Bug UDP Client, when reading a new message, the PeerIP and PeerPort was not set.
 [*] : Fixed Bug Binance API Client, error EConvertError when calling NewOCO method.
 [*] : Fixed Bug Binance API Client, the method CancelAllOpenOrders was calling the wrong method (Thanks to Stefano to let me know).
 [*] : Fixed Bug SQS Component encoding/decoding special characters (Thanks to Erik to let me know).
 [*] : Fixed Bug compiling under Linux64.

 [/] : Method sgcWebSocket_Helpers.sgcContainsText moved to sgcBase_Helpers.sgcContainstText.
 [/] : STUN Server Event OnSTUNRequestSuccess has been modified.
 [/] : STUN Server Event OnSTUNRequestError has been modified.
 [/] : STUN Client Event OnSTUNResponseSuccess has been modified.
 [/] : STUN Client Event OnSTUNResponseError has been modified. 
 [/] : Telegram, RCON and Cryptohopper clients have been moved from unit sgcWebSocket_APIs to sgcLibs.




## 4.5.1: 2021 July

 [+] : New Component TsgcLib_RCON, is a TCP/IP-based communication protocol which allows console commands to be issued to the server.
 [+] : New Demo which shows how to use the RCON Client, is located in the folder "50.Other\02.RCON".
 [+] : New Component TsgcHTTP_Cryptohopper, it's a crypto trading bot and portfolio manager. 
 [+] : New Demo which shows how to use the CryptoHopper Client, is located in the folder "50.Other\03.Cryptohopper". 
 [+] : Improved Binance Futures API, new method "PlaceTrailingStopOrder", places a new Trailing Stop Order to Binance Future Server.
 [+] : Improved SChannel, new property "CipherList" in TLSOptions.SChannel_Options, which allows to set the cipher list used to connect to a secure server. Example: CALG_AES_256:CALG_AES_128
 [+] : Improved SChannel, new method "GetInfo" allows to get the connection info properties like Transport, Cipher, Exchange...
 [+] : Improved TsgcWebSocketClient, WebSocket redirections are now supported by websocket client.

 [*] : Fixed Bug compiling CBuilder package, "CryptStringToBinaryW" not found.
 [*] : Fixed Bug MQTT Protocol and WatchDog.Attempts > 0, after a reconnection, the internal Attempts count value was not cleared.
 [*] : Fixed Bug MQTT Protocol, when QoS = mtqsExactlyOnce, after receiving a PubRel message, the PubComp reply was not sent.
 [*] : Fixed Bug MQTT Protocol, when QoS = mtqsExactlyOnce, the stored message was not deleted when PUBCOMP message was received. 
 [*] : Fixed Bug OnException event when notifyEvents = neAsynchronous, in some cases the Exception parameter was already destroyed.
 [*] : Fixed Bug Binance Futures API, when calling ChangeInitialLeverage returns the error "mandatory parameter timestamp was not sent".
 [*] : Fixed Bug WebRTC wasn't working using HTTP/2 as protocol.
 [*] : Fixed Bug connecting to Apple APNs using SChannel.
 [*] : Fixed Bug WatchDog, if the client was disconnected and set Active = False, the watchdog never stops if WatchDog.Attempts = 0.
 [*] : Fixed Bug Clearing internal Ping List, an access violation can happen in some cases.
 [*] : Fixed Bug STUN Server, the magic cookie was not included in the response message.
 [*] : Fixed Bug Bug Binance API, StartTime and EndTime parameters have been updated from Integer to Int64.
 [*] : Fixed Bug HTTP.SYS Server, when Asynchronous = True and the message sent size was more than 500KB an internal error was raised and the connection was closed.
 [*] : Fixed Bug SignalR Client, when the SignalR Server is listening in a URL with parameters the client cannot connect to server.




## 4.5.0: 2021 June

 [+] : New Component TsgcSTUNServer, implements the STUN Server Protocol providing a service to discover the mapped IP Address and port number.
 [+] : New Component TsgcSTUNClient, implements the STUN Client Protocol.
 [+] : New Demo which shows how use STUN Server and Client, is located in folder "35.P2P\02.STUN".
 [+] : New Component TsgcWSAPI_FTX, client component with support for FTX Broker Crypto trading. Supports: 
       - WebSocket Public and Private Channels.
	   - REST Public and Private Endpoints. 
 [+] : New property "BoundPortMin" and "BoundPortMax" in TsgcWebSocketClient, allows to set the min and max local port used by websocket client.
 [+] : New property "LingerState" in TsgcWebSocketClient, allows to reset a socket connection where LingerState = 0. By default the value is -1, which means the connection will be closed gracefully.
 [+] : Modified Publish method of Google PubSub, now has a new parameter called "aOrderingKey" where you can set the name of the attributes which is the key. 
 [+] : Improved HTTP.SYS Server, if Watchdog.Monitor is enabled server is SSL, the client monitor uses SChannel instead of OpenSSL.
 [+] : Improved Binance API, new property "TestNet", if enabled will connect to the Binance Demo Account.
 [+] : Improved Binance Spot API client component, new methods: CancelAllOpenOrders, PlaceMarketOrder, PlaceLimitOrder and PlaceStopOrder.
 [+] : Improved Binance Futures API client component, new methods: PlaceMarketOrder, PlaceLimitOrder and PlaceStopOrder.
 [+] : Improved WinHTTP WebSocket Client, implemented Connect and Disconnect methods to wait till client is connected/disconnected from server.
 [+] : Improved WinHTTP WebSocket Client, implemented Start and Stop methods which connect/disconnect from server using a secondary thread avoiding freezing the main thread.
 [+] : Improved Telegram API, method GetSupergroupMembers now can be filtered by Administrator, Bots, Contacts...
 [+] : Improved OAuth2 Server, new method "AddToken" allows to recover issued tokens when the OAuth2 server is restarted.

 [*] : Fixed Bug Google PubSub, if the published messages have attributes, the attributes weren't double quoted.
 [*] : Fixed Bug HTTP.SYS Server, the CustomHeaders set in the HTTP Response were not included in the HTTP Response Headers.
 [*] : Fixed Bug HTTP.SYS Server, the ContentStream was not included in the HTTP Response Body.
 [*] : Fixed Bug when Options.RaiseDisconnectException was true, the event was raised in the context of the connection thread even if notifyEvents <> neNoSync.
 [*] : Fixed Bug compiling under FPC and ARM, there was a thread-lock using the latest indy version.
 [*] : Fixed Bug HTTP.SYS Server, the LogFile.FileName was not editable at design-time.
 [*] : Fixed Bug HTTP.SYS Server, memory leak when the connection was disconnected.
 [*] : Fixed Bug WinHTTP WebSocket Client (asynchronous = true) the buffersize was fixed instead of using ReceiveBufferSize property.
 [*] : Fixed Bug WinHTTP WebSocket Client (asynchronous = true) if there was an error during websocket handshake an unhandled exception was raised.
 [*] : Fixed Bug when TsgcWebSocketClient has attached some API, if the OnDisconnect internal event had an exception while processing, the event was not called.
 [*] : Fixed Bug Telegram API when Document.FileName has utf-8 characters.

 [/] : Renamed Property TsgcWebResponseHTTPAPI.CustomHeader to TsgcWebResponseHTTPAPI.CustomHeaders.
 [/] : Modified function PlaceStopOrder of Coinbase API Client.
 [/] : Modified Book Depth value "bde15" to "bde20".
 [/] : Renamed OAuth2 Server function "GetApp" to "GetAppByClientId".



## 4.4.9: 2021 May

 [+] : New property "HttpUploadFiles" in HTTP Servers (TsgcWebSocketHTTPServer and TsgcWebSocketServer_HTTPAPI). Allows to save the POST streams received as FileStreams so server can receive big files without getting out of memory exception.
 [+] : New Demo that shows how POST big Files and store in a file instead of memory using WebSocket HTTP Server.
 [+] : New Demo Apple Push Notifications, shows how send push notifications to apple devices using HTTP/2 and Certificates or JWT as authentication.
 [+] : New Component TsgcUDPClient, UDP client based on Indy library for UDP connections.
 [+] : New Component TsgcUDPServer, UDP server based on Indy library for UDP connections.
 [+] : New Demo which shows how use UDP Server and Client, located in folder "Demos\01.WebSocket_Quick_Start\11.UDP_Server_Client".
 [+] : Improved OAuth2 Client, now supports OAuth2 Client Credentials (for applications like daemons or service accounts). There is a new property called GrantType with the following values (auth2Code, auth2ClientCredentials).
 [+] : Improved OAuth2 Client Demo, new Configuration "Azure AD As Service" showing the use of new Client Credentials grant type.
 [+] : Improved OpenSSL_Options property, new property "LibPath", if has the value "oslpDefaultFolder" automatically calls IdOpenSSLSetLibPath and sets the default lib folder.
 [+] : Updated Indy for Lazarus to latest version.
 [+] : Update OpenSSL libraries 1.1.1 to latest version.

 [*] : Fixed Bug HTTP/2 Server sending Windows Update Frame.
 [*] : Fixed Bug OAuth2 Client error opening WebBrowser under MacOSX.
 [*] : Fixed Bug compiling sgcWebSockets under ios, error linking JWT openSSL methods. By default JWT is disabled under iOS, enable SGC_JWT_IOS in sgcVer.inc.
 [*] : Fixed Bug HTTP client was not setting the correct openSSL API value.
 [*] : Fixed Bug Loading openSSL 1.1 under OSX64.
 [*] : Fixed Bug HTTP.SYS Range Check Error when RangeChecking is enabled. 
 [*] : Fixed Bug SChannel if no certificate was found by issuer, the connection was closed.
 [*] : Fixed Bug TsgcWebSocketServer and TsgcWebSocketHTTPServer, if authentication was enabled an access violation was raised processing any request.
 [*] : Fixed Bug Binance Futures API calling method "GetPositionInformation", binance server was returning 404 error.
 [*] : Fixed Bug Google PubSub client, JSON message creading calling Publish Method with arguments was incorrect. (Thanks to Erik to let me know):

 [/] : Updated Binance Futures REST API, the method "GetAllLiquidationOrders" has been deleted because is not supported any more by Binance API.



## 4.4.8: 2021 April

 [+] : New Component TsgcHTTP_JWT_Client, allows to encode and sign JWT Tokens as Authentication Bearers in HTTP/1, HTTP/2 and WebSocket Client Components.
 [+] : New Component TsgcHTTP_JWT_Server, allows to decode and validate JWT Tokens as Authentication Bearers in HTTP/1, HTTP/2 and WebSocket Server Components.
 [+] : New Component TsgcWSAPI_Kraken_Futures, Kraken client component to get futures market data. Supports: 
       - WebSocket Public and Private Channels.
	   - REST Public and Private Endpoints.
 [+] : Improved Coinbase Pro API, now Rest API is fully supported, so you can trade: place market orders, limit orders, cancel orders, list orders...
 [+] : Improved Coinbase Pro API, WebSocket API now supports user channel.
 [+] : Improved Coinbase Pro API, New Property "SandBox" which allows to test trading account without real funds.
 [+] : Improved LogFile in WebSocket Server and Client components, now websocket messages are logged unmasked.
 [+] : Improved Telegram API, new Methods: GetBasicGroupFullInfo, GetSupergroupMembers and GetChatMember, allow to get members information of Basic and Super groups.
 [+] : Improved TsgcWebSocketHTTPServer, new property "Charset" where you can set the default Charset of DocumentRoot files served.
 [+] : Improved OpenSSL 1.1.1, reading certificates with password, now doesn't require enable the compiler define "SGC_OPENSSL_API_1_1" in IdCompilerDefines.inc
 [+] : Improved SSLOptions.OpenSSL_Options.ECDHE property of WebSocket Server, now if enabled adds a secure cipherlist for TLS 1.2.
 [+] : Improved Binance Client, if a message is received from Binance informing that ListenKey has expired, automatically requests a new ListenKey.

 [*] : Fixed Bug WebSocket protocol reading UTF8 message using Delphi 7 to 2009 and with latest indy version.
 [*] : Fixed Bug Google PubSub Client, messages were encoded as ASCII instead of UTF-8.
 [*] : Fixed Bug Binance API converting LocalTime to UNIX UTC Time.
 [*] : Fixed Bug HTTP/2 Client, Headers argument of OnHTTP2BeforeRequest event wasn't initialized.
 [*] : Fixed Bug HTTP/2 Server, detecting HTTP/2 protocol fails if buffer contains more than 1 frame.
 [*] : Fixed Bug OAuth2 Client, passing username/password returns an Access Violation assigning values to HTTP client. (Thanks to Peter to let me know).
 [*] : Fixed Bug Range Check Error (when RangeChecking is enabled in Compiler options) in HTTP/2 protocol.
 [*] : Fixed Bug converting Integer to array of bytes in HTTP/2 protocol.
 [*] : Fixed Bug HTTP/2 Client, openSSL libraries 1.0.2 were loaded instead of 1.1.1 when APIVersion = oslAPI_1_1.
 [*] : Fixed Bug HTTP/2 Client, event OnHTTP2GoAway, the parameter GoAway wasn't assigned when notifyEvents = neAsynchronous.
 [*] : Fixed Bug HTTP/2 Client, event OnHTTP2RSTStream, the parameter RSTStream wasn't assigned when notifyEvents = neAsynchronous.
 [*] : Fixed Bug TLS 1.3 and OpenSSL 1.1.1, by default set the minimum protocol to TLS 1.0 instead of TLS 1.2 

 [/] : Changed PSSL_CTX to Pointer, to allow both APIs: openSSL 1.0.2 (PSSL_CTX_1_0) and openSSL 1.1.1 (PSSL_CTX_1_01) 



## 4.4.7: 2021 February

 [+] : New Client Component TsgcWSAPI_Coinbase, Coinbase pro is an US-based crypto exchange. Trade Bitcoin (BTC), Ethereum (ETH), and more for USD, EUR, and GBP. Support for WebSocket API and REST API.
 [+] : Improved Demo 01.WebSocket_Quick_Start\02.WebSocket_Clients_APIs, a new Tab has been added to show how works Coinbase API.
 [+] : Improved Binance Futures API, new property FutureContracts which allows to trade with USDT or COIN futures.
 [+] : Improved Demo 01.WebSocket_Quick_Start\02.WebSocket_Clients_APIs, now Binance Futures allows to select USDT or COIN futures.
 [+] : New Demo 02.WebSocket_Protocols\09.Binance_Trade_Futures, shows how to place an order using Binance Futures API. 
 [+] : Improved WebSocket Client, new event "OnBeforeConnect" this method is called before the client tries to connect to server.
 [+] : Improved WebSocket Client, new event "OnBeforeWatchDog" allows to customize the Client before the client tries to reconnect to server.
 [+] : Improved TsgcWebSocketHTTPServer, new property HTTP2Options.AltSvc, if enabled informs to client that HTTP/2 is supported by server.
 [+] : Improved OAuth2 Client, LocalServer supports SSL/TLS connections (only professional and enterprise editions).
 [+] : Improved Telegram client, new method SendRichTextMessage with support for bold, italic, underline, strike and code formats.
 [+] : Improved Telegram client, new method GetChat which allows to get the data of a single chat (supported by user and bots).
 [+] : Improved Socket.IO API Client, added support for Socket.IO 3.* API.
 [+] : Improved HTTP/2 Client, when doing a Synchronous Request, the property Response saves the Headers and Content of the HTTP/2 Response.
 [+] : Improved HTTP/2 Client, SChannel is now supported.
 [+] : Improved SChannel, now supports the use of Certificates: using a Certificate in PFX format or a Certificate Hash thumbprint.
 [+] : New Client Component TsgcHTTP1Client (non-visual) which inherits from TIdHTTP Indy client HTTP and adds features like: TLSOptions (OpenSSL and SChannel), Log to file and Authentication.

 [*] : Fixed Bug compiling on CBuilder, error in sgcWebSocket_WinAPI unit ERROR_HTTP_INVALID_SERVER_RESPONSE.
 [*] : Fixed Bug compiling on CBuilder, ambiguity between _ULARGE_INTEGER and WebView2 _ULARGE_INTEGER, same for wrSignaled. (Thanks to Franz to let me know).
 [*] : Fixed Bug using SChannel as IOHandler and connecting through a Proxy Server. (Thanks to Anders to let me know).
 [*] : Fixed Bug "EVP_MD_CTX_Create is not a declared identifier" compiling with "SGC_OPENSSL_API_1_1" compiler directive enabled. (Thanks to Michael to let me know).
 [*] : Fixed Bug TsgcWebSocketClient getting the Active property value was sometimes slow or locked.
 [*] : Fixed Bug TsgcWebSocketClient ProxySocks connect directly to server instead of use Proxy Server.
 [*] : Fixed Bug Binance Rest API format of currency values wasn't properly set.
 [*] : Fixed Bug Binance error "TLSv1 alert protocol version" when sending a KeepAlive Request for UserStream. (Thanks to Wouter to let me know).
 [*] : Fixed Bug Binance Order type has been updated from Int32 to Int64.
 [*] : Fixed Bug Kraken Rest API format of currency values wasn't properly set.
 [*] : Fixed Bug TsgcWebSocketHTTPServer, DocumentRoot wasn't working when using HTTP/2 protocol.
 [*] : Fixed Bug HTTP/2 Client, when client cannot connect to server during a Synchronous request, the event OnHTTP2Exception was not called.
 [*] : Fixed Bug HTTP/2 Client error "Range out of Bounds" running under windows64.
 [*] : Fixed Bug HTTP/2 Client doing a Synchronous request insed a TTask method. (Thanks to Ralph to let me know).
 [*] : Fixed Bug HTTP/2 Server, connection was closed incorrectly trying to detect an invalid WindowUpdate value.
 [*] : Fixed Bug HTTP/2 reading single Frame in different tcp packets.
 [*] : Fixed Bug HTTP/2 Client memory leaks doing Synchronous requests.
 [*] : Fixed some compiler warnings.

 [/] : ProxyType property [pxSOCKS] has been deleted and splitted in 3 values [pxySocks4, pxySocks4A, pxySocks5]



## 4.4.6: 2021 January

 [+] : New Event OnBeforeForwardHTTP on Server Components, allows to forward an HTTP request to another server. (Thanks to Olaf for his suggestion).
 [+] : New Event OnAfterForwardHTTP on Server Components, allows to know the response from HTTP Forwarded Request.
 [+] : Improved TsgcWebSocketHTTPServer, now has support for HTTP/2 Server Push using PushPromiseAddPreLoadLinks method to configure the push promise files.
 [+] : Improved TsgcWebSocketHTTPServer, added support for HTTP/2 cookies.
 [+] : Improved TsgcWebSocketHTTPServer, new Property HTTP2Options.Events, configures if Connect/Disconnect events are called under HTTP/2 protocol (by default are disabled).  
 [+] : New Property ReadBufferSize in HTTP.SYS Server, allows to set the size of the read buffer, by default is 16384.
 [+] : Improved Telegram API, send bot messages with buttons (Callback and Url) is now supported.
 [+] : Improved Telegram API, a new event "OnNewCallbackQuery" has been added, allows to process which buttons have selected the users.
 [+] : Improved Google PubSub API, now supports service accounts using JWT as Authentication.
 [+] : Improved MQTT client, HeartBeat now supports Timeout, if after x time the client doesn't receive a response to the ping previously sent, it closes the connection automatically.

 [*] : Fixed Bug writing ALPN protocol when FastMM4 is enabled.
 [*] : Fixed Bug Out of Memory when HTTP/2 and FastMM4 are enabled reading internal Frames.
 [*] : Fixed Bug in Indy Servers, the ReadTimeOut value was not used after read socket data to check if there was more data to process.
 [*] : Fixed Bug TsgcHTTP2Client when received a RSTStream, the event wasn't assigned and an access violation was raised.
 [*] : Fixed Bug Azure IoT MQTT Client when passing a property with the "/" character, it wasn't encoded properly.
 [*] : Fixed Bug Access Violation when closing HTTP.SYS server (if SSL was enabled) under x64 and FastMM5 was enabled.
 [*] : Fixed Bug when assigning a thread-name under DEBUG, in some cases, the thread name was assigned to incorrect thread.
 [*] : Fixed Bug Basic Authorization was not read under HTTP/2 protocol if Authentication was not enabled.
 [*] : Fixed Bug Server HTTP/2 Protocol reading a Window_Update while Header Frame was not already processed.
 [*] : Fixed Bug HTTP/2 Protocol, connection window update was not updated and an error was raised closing connection.
 [*] : Fixed Bug HTTP/2 Protocol decoding latest header of Static table.
 [*] : Fixed Bug HTTP/2 Protocol receiving unexpected stream identifier in client component.
 [*] : Fixed Bug Google Calendar Client access violation when reading default reminders.
 [*] : Fixed Bug TsgcWebSocketClient if Options.CleanDisconnect = True and there was an error sending the close message, the disconnect event wasn't called.
 [*] : Fixed Bug TsgcWebSocketClient, avoid potential thread-lock when reconnecting to server if notifyEvents = neNoSync. (Thanks to Stefan to let me know).
 [*] : Fixed Bug TsgcWebSocketClient, avoid potential call to OnDisconnect event twice.
 [*] : Fixed Bug Memory Leak on Telegram Client.
 [*] : Fixed Bug SignalR client, invalid variant error if connects to a non SignalR server.
 [*] : Fixed Bug SignalR client, potential invalid variant error decoding ConnectionTimeout.
 [*] : Fixed Bug LogFile of TsgcWebSocketClient wasn't thread safe. (Thanks to Eddy to let me know).
 [*] : Fixed Bug TsgcWebSocketClient using TLS 1.3 sometimes an error was raised when connecting to server.

 [/] : TsgcWebSocketClient.FWSConnection is now cleared BEFORE OnDisconnect event is called.


## 4.4.5: 2020 December

 [+] : New Component TsgcHTTP_OAuth2_Server, server implementation of OAuth2 protocol, allows to Authorize and Issue Access Tokens to OAuth2 clients.
 [+] : New Demo which shows how enable OAuth2 on Server Components (is located in folder Demos\20.HTTP_Protocol\02.OAuth2_Authentication).
 [+] : Improved Azure IoT MQTT Client, now DeviceToCloud allows to send Properties in the Message (are key-value pairs).
 [+] : New Property HTTPClientOptions in TsgcHTTP_OAuth2_Client, allows to customize the HTTP Client when requests a new token.
 [+] : New Property BindingOptions in HTTP.SYS Server, allows to customize if server Configures the SSL Certificate when starts (requires admin rights) or not. By default is enabled.
 [+] : New Event "OnBeforeBinding" in HTTP.SYS Server, allows to customize the URLs will be reserved by Server.
 [+] : Improved TsgcWebSocketClient_WinHTTP, new property Options.FragmentedMessages which works like TsgcWebSocketClient.
 [+] : Improved TsgcWebSocketClient_WinHTTP, new event OnFragmented.
 [+] : New Property ConnectHeaders in TsgcWSPClient_STOMP, allows to send custom headers on connect method.

 [*] : Fixed Bug Invalid Pointer when NotifyEvents = neAsynchronous and CheckSynchronize was called while the event was processing. (Thanks to Dirk to let me know)
 [*] : Fixed Bug Processing Fragmented Messages, first fragmented was overwrited when second fragment arrived. (Thanks to Patrik to let me know)
 [*] : Fixed Bug TsgcWebSocketClient when there was a disconnection, internal threads were stopped, but this method was called several times in some cases.
 [*] : FIxed Bug potential Thread-Lock when NotifyEvents = neAsynchronous, connection was disconnected and there were messages pending to be processed.
 [*] : Fixed Bug Access Violation error executing method "Start" when Client/Server was already destroyed.
 [*] : Fixed Bug TsgHTTP_OAuth2, after receiving authorization code, state value was not compared against value send, now if is not equal returns an error.
 [*] : Fixed Bug Telegram Client, the read thread didn't start after connect to telegram servers.
 [*] : Fixed Bug Telegram Client, the Title of the chat message wasn't properly decoded. (Thanks to Hyeonwoo to let me know).
 [*] : Fixed Warnings compiling from Rad Studio XE8 to 10.1 Berlin
 [*] : Fixed Bug Indy Servers, if connection was already closed but Buffer had still data to process, the thread never ends and make use of full cpu.
 [*] : Fixed Bug HTTP.SYS Server, if OnHTTPRequest event wasn't set, there wasn't any response from server, now returns a 404 error.
 [*] : Fixed Bug HTTP.SYS Server decoding HTTP methods, only GET and POST were supported.
 [*] : Fixed Bug HTTP.SYS Server, memory leak when destroying a connection in TsgcWSMSG object.
 [*] : Fixed Bug HTTP.SYS Server, invalid pointer exception trying to free an object while disconnecting.
 [*] : Fixed Bug HTTP.SYS Server, when there was an error starting the server, the real error message wasn't raised to user.
 [*] : Fixed Bug in TsgcWSAPI_SocketIO component when initializing connection and ioAPI0 is selected as API (Thanks to Jean to let me know).
 [*] : Fixed Bug connecting when WriteTimeOut > 0 on none Windows OS, now this property only applies to Windows.

 [/] : TsgHTTP_OAuth2 component renamed to TsgcHTTP_OAuth2_Client.
 [/] : Unit sgcHTTP_OAuth.pas renamed to sgcHTTP_OAuth_Client.pas
 [/] : Unit sgcHTTP_OAuth2.pas renamed to sgcHTTP_OAuth2_Client.pas


## 4.4.4: 2020 November

 [+] : New Component TsgcHTTPGoogleCloud_Calendar_Client, allows to use Google Calendar API V3: get Calendars, events, synchronize with your own calendar...
 [+] : New Demo GoogleCalendar which shows the main features of Google Calendar Client.
 [+] : New method "PublishAndWait" in MQTT Client, this method allow to publish a message using mtqsAtLeastOnce or mtqsExactlyOnce and wait till message is processed by server.
 [+] : New method "SendAndWait_DeviceToCloud" in Azure IoT MQTT Client, sends a message from device to cloud and wait till server processes the request.
 [+] : New Property Authentication in TsgcHTTP2Client, allows to send HTTP/2 Requests using OAuth2 protocol as authentication.
 [+] : Improved HTTP/2 Server, ping and heartbeat are now supported.
 [+] : Improved Google PubSub client, new Events "OnAuthToken" and "OnAuthTokenError" allows to handle the OAuth2 event flow.
 [+] : Improved Google PubSub client, new Method "RefreshToken" allows to reconnect to an OAuth2 session.
 [+] : Improved Telegram Client, added support for proxies: HTTP, MTProto and Socks5. New methods to Add Proxies, Remove, Enable, Disable...
 [+] : New method "Restart" in Server Components, restart the server in a secondary thread.
 [+] : Improved WatchDog on Server components, a new property called Monitor, if enabled, a client will try to connect to server, if fails after the TimeOut set, the server is restarted automatically.

 [*] : Fixed Bug TsgcWebSocketClient and TLSOptions.IOHandler = iohSChannel, when closing connection an exception 10004 was shown. 
 [*] : Fixed Bug TsgcWebSocketClient and TLSOptions.IOHandler = iohSChannel, when destroying TsgcWebSocketClient if connection was active, a thread-lock occurs.
 [*] : Fixed Bug Azure IoT MQTT Client, OnMQTTPubAck wasn't be called when client receives an acknowledgement from server.
 [*] : Fixed Bug Server connections wasn't closed if OriginsAllowed not match the websocket origin client.
 [*] : Fixed Bug ServerSentEvent javascript code, contains invalid text.
 [*] : Fixed Bug compiling Custom Indy version, sgcIdStackVCLPosix was using IdCTypes instead of sgcIdCTypes.
 [*] : Fixed Bug HeartBeat, if there was an exception sending a ping, exception was not captured and was shown to user.
 [*] : Fixed Bug MQTT Client, if there was an exception while resending a message with Qos <> mtqsAtLeastOnce, exception was not captured and was shown to user.
 [*] : Fixed Bug MQTT Client, when publishing a Stream with Qos <> mtqsAtLeastOnce and not received an acknowledgment from server before timeout, when resend the message, payload was empty.
 [*] : Fixed Memory Leaks on Server Component when HTTP/2 is enabled.
 [*] : Fixed Bug HTTP/2 when the other peer send a InitialWindowSize settings update.
 [*] : Fixed Bug HTTP/2 Client, if during a Synchronous HTTP Request, there was a disconnection, client didn't stop wait a result.
 [*] : Fixed Bug HTTP/2 Server, if SETTINGS_INITIAL_WINDOW_SIZE was changed after HEADERS, the WindowSize was not adjusted properly.
 [*] : Fixed Bug Binance Spot User Stream API, if there was an error deleting internal ListenKey after a disconnection, the field was not cleared and can't reconnect.
 [*] : Fixed Bug WatchDog on Server Components, if the server was stopped manually, the WatchDog try to start server again instead of stop.
 [*] : Fixed Bug compiling sgcJSON_XSuperObject and sgcJSON_System with Delphi 10.4
 [*] : Fixed Bug WebSocket Indy Servers, if Options.ReadTimeOut = 0 the server make use of full cpu. Now the minimum value for ReadTimeOut = 1
 [*] : Fixed Bug Websocket Indy Servers, if server send a close packet and it's not received/processed by other peer, the connection make use of full cpu.

 [/] : TsgcHTTP2Client HTTP/2 Asynchronous methods, now are renamed to GetAsync, PostAsync, PutAsync...
 [/] : Demos now are grouped by categories.



## 4.4.3: 2020 October

 [+] : Initial support for HTTP/2 in TsgcWebSocketHTTPServer
       - New property HTTP2Options: allows to enable HTTP/2 protocol and configure initial settings.
 [+] : Improved Bittrex API component, now supports latest V3 API.
       - New Methods: Subscriptions to Balance, Orders, Candles, Trades...
	   - New Events: OnAuthenticated, OnHeartBeat, OnUnSubscribed...
 [+] : New Event OnBeforeHeartBeat on Client and Server components, allows to customize HeartBeat behaviour.
 [+] : New Non-Visual component TsgcWebBrokerBridgeRequestHandlerHTTP2, it's a server replacement for DataSnap WebBrokerBridge with support for HTTP/2 Connections.
 [+] : New Property SignatureV4 on Amazon IoT MQTT Client, allows to connect using port 443 and don't make use of certificates.
 [+] : New Property CustomAuthentication on Amazon IoT MQTT Client, allows to connect using port 443 (over TCP or WebSockets) and authenticate using URL Parameters or Header Fields.
 [+] : New Properties on Amazon and Azure IoT MQTT Clients.
       - MQTTHeartBeat: allows to send a ping automatically every X seconds.
       - WatchDog: allows to reconnect automatically after an undesired disconnection.
       - LogFile: allows to log protocol messages in a file for debug purposes. 
 [+] : New Property MQTTAuthentication on Amazon IoT MQTT client, allows to set the username and password when connects to server.
 [+] : New Property SAS.Expiry on Azure IoT MQTT Client, allows to set the time in minutes before the SAS Token expires.
 [+] : Improved HTTP/2 demo, a new server has been added for performance testing.
 [+] : Improved Server Chat Demo to show how enable HTTP/2 connections.

 [*] : Fixed Access Violation TsgcWebSocketClient when TLS is enabled reading bytes from socket.
 [*] : Fixed Access Violation when WebSocket server uses SSL and is disconnecting.
 [*] : Fixed Bug Socket.IO, connection was closed by a HeartBeat timeout.
 [*] : Fixed Bug Reading Compressed Frame when Compression was enabled.
 [*] : Improved Memory Usage when Compression is enabled.
 [*] : Fixed Bug TsgcHTTP2Client high use of cpu while idle.
 [*] : Fixed Bug TsgcHTTP2Client when switching to another server and request was asynchronous, the connection was frozen.
 [*] : Fixed Bug Azure IoT MQTT Client, when reconnect using watchdog, the SAS token was not set properly.
 [*] : Fixed Bug Dataset Protocol when formatsettings were different between peers.
 [*] : Fixed Bug SignalRCore Client, high consume cpu while waiting a response from server.
 [*] : Fixed Bug TsgcWebSocketServer/TsgcWebSocketHTTPServer, high consume cpu when IOCP was enabled.
 [*] : Fixed Bug TsgcWSServer_HTTPAPI_WebBrokerBridge when assigning a Stream response.

 [/] : Bittrex API Client Component has changed several methods and events due to update to latest API V3.



## 4.4.2: 2020 September

 [+] : New Component TsgcHTTP2Client, fully featured HTTP/2 client (*Requires custom Indy version). Main features supported:
       - Supports All Rad Studio Personalities (windows, MacOSX, Android, iOS and Linux)
	   - Can work in fully Asynchronous mode or blocking mode.
	   - Supports Multiplexed streams.
       - Server Push.
	   - Partial Responses.
	   - HeartBeat, Automatic Reconnection ... and more.
 [+] : Improved Telegram API Component, added support for iOS64.
 [+] : New Component TsgcWSAPI_Binance_Futures, Binance client component to get futures market data. Supports: 
       - WebSocket Market Streams
	   - Account / Trade Endpoints
	   - User Data Streams
 [+] : Improved Performance when queues are enabled, now if there is no items in the queue thread isn't unlocked/locked. (Thanks to Michael for suggestion).

 [*] : Fixed Bug Telegram Component was not installed under Lazarus + Linux.
 [*] : Fixed Bug MQTT Protocol can't connect to MQTT Broker (only affects to Delphi 2009).
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, when Async = True, trying to send a message just after client connects always fails.
 [*] : Fixed MemoryLeak using ALPN protocol.
 [*] : Fixed Bug in Static OpenSSL unit, some methods were incorrectly defined. (Thanks to S?bastien for his patch). 
 [*] : Fixed Bug Discord API, sending HTTP Post without UTF8 Encoding, returns a HTTP error. (Thanks to Adriaan for his patch).



## 4.4.1: 2020 July

 [+] : Improved Telegram API Component, added support for Android64.
 [+] : New property "DatabaseDirectory" in Telegram Client. Allows to set the directory where is the TDLib database.
 [+] : Improved Telegram Demo to ask user for a password if telegram component requires it.
 [+] : Improved speed reading websocket data (requires Delphi 2010+) applies to server and client components.
 [+] : Threads now are identified by classname or classname + Connection.Guid while Debug is active.
 [+] : New Property TimeOut in Indy IOCP Server, allows to set the max timeout closing server threads.
 [+] : Updated OpenSSL Custom Indy, added X509_verify_cert_error_string to be able to retrieve cert error. (Thanks to S?bastien for his patch).
 [+] : Improved Dataset Protocol, there is a new property "FormatSettings" to set the format settings of float and datetime fields (avoiding different format settings between peers).
 [+] : Added support for ALPN (Application-Layer Protocol Negotiation) when SChannel is set in TsgcWebSocketClient.
 [+] : New property "Path" in Socket.IO API. Allows to set custom path before connecting to socket.io Server. 


 [*] : Fixed Bugs Compiling CBuilder 2010.
 [*] : Fixed Bug Rad Studio 10.4 destroying objects in nextgen compilers.
 [*] : Fixed Bug compiler config file wasn't including telegram component.
 [*] : Fixed Bug MQTT 5.0 API reading PubACK, PubREC, PubREL, PubCOMP Properties.
 [*] : Fixed Bug MQTT 5.0 Calling publish method and passing properties as parameter.
 [*] : Fixed Bug Indy Server + IOCP, access violation closing connection.
 [*] : Fixed Bug Indy Server + IOCP, exception "connection closed gracefully" was showed to end-user.
 [*] : Fixed Bug Indy Server + IOCP, memory leaks have been removed.
 [*] : Fixed Bug TsgcWebSocketClient.Connect, if remote peer was not available, an exception was raised.
 [*] : Fixed Bug MQTT Client Protocol, when watchdog is enabled and Attempts value is greater than zero, client was trying to reconnect more times than the attempts value.
 [*] : Fixed Bug OpenSSL Custom Indy, for openssl 1.1.1 use EVP_MD_CTX_new and EVP_MD_CTX_free. (Thanks to S?bastien for his patch).
 [*] : Fixed Bug OpenSSL Custom Indy, changed wrong name for sk_pop_free and added some functions available for static linking. (Thanks to S?bastien for his patch).
 [*] : Fixed Bug Compiling sgcWebSockets + Custom Indy under Linux. (Thanks to Hans for his patch).
 [*] : Fixed Bug TsgcWebSocketClient when Server sends a Sub-protocol which client has not requested.
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, when Async = True and TLS is enabled, client cannot connect to server.
 [*] : Fixed Bug Presence Protocol, if while disconnecting, a member was not found and exception was raised. (Thanks to Michael to let me know).
 [*] : Fixed Bug Intraweb Client sending a message with Intraweb XV.
 [*] : Fixed Bug Thread Lock while Client Disconnecting when TLS is enabled with latest Indy version.
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, binary messages were not read properly in the latest versions of Delphi / CBuilder.
 [*] : Fixed Bug Azure IoT Client, it couldn't connect depending of Timezone configuration.
 [*] : Fixed Bug Telegram component, SetTDJsonPath was not set as public method.
 [*] : Fixed Bug Presence Protocol Javascript sending characters like double quote in json messages.
 [*] : Fixed Demo Socket.IO, it wasn't working because server url was changed.

 [/] : Deleted Deprecated TsgcWebSocketClient_SocketIO. Now socket.io is only available as an API.
 [/] : Changed Binance HTTP Enumerations to avoid conflict with WebSocket Enumerations.
 [/] : Changed Kraken HTTP Enumerations to avoid conflict with WebSocket Enumerations.


## 4.4.0: 2020 June

 [+] : Added support for Rad Studio 10.4 Sydney.
 [+] : Improved Telegram API Component, added support for OSX64.
 [+] : Improved Telegram API Component, added support for Linux64.
 [+] : Improved Telegram API Component, use SetTDJsonPath to set the path of tdjson library.
 [+] : New Telegram Demo built with Firemonkey.
 [+] : Improved Dataset Protocol, added a new value to UpdateMode, "upRefreshAll", if selected, every time there is a dataset change, instead of edit dataset, it updates (useful when server and clients share the same database).
 [+] : New Property TLSOptions.VerifyDepth for Server and Client components, is the maximum number of intermediate certificate issuers (default value is zero).
 [+] : New Coturn server is now provided as a compiled console application for windows. Coturn is a STUN/TURN server for WebRTC protocol.
 [+] : Improved WAMP 1.0 Protocol, now implements progress calls. A client request a server method, and server returns response in several results. WAMP Demo has been updated to show how works.
 [+] : Improved Ping method, if ping is called manually, now you can pass the string of the ping message.
 [+] : Improved Server Plain TCP Connections, if HeartBeat is enabled, it will send a message to maintain connection.
 [+] : New Demo IOCP, which shows how Indy IOCP Simple Server works.
 [+] : New Event OnTCPConnect in Indy Server, this event is called after a TCP Connection and before WebSocket HandShake.

 [*] : Critical Bug, 4.3.7 version introduced a bug when NotifyEvents is neAsynchronous or neSynchronous, when several messages were received at the same time, the events were not dispatched correctly and the messages become corrupted.
 [*] : Fixed Bug Telegram Client, error parsing telegram message, MessageId was defined as Integer instead of Int64.
 [*] : Fixed Bug Custom Indy + OpenSSL 1.1, if certificate has a password, it can't be loaded. Fix requires enable in IdCompilerDefines.inc, compiler directive SGC_OPENSSL_API_1_1.
 [*] : Fixed Bug Custom Indy, error compiling when OPENSSL_NO_MD4 or OPENSSL_NO_MD5 compiler defines were enabled. (Thanks to S?bastien to let me know).
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, Built-in html files were not server if SSL was enabled.
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, if Authentication was enabled, sometimes request was not processed correctly.
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, an internal buffer wasn't correctly initialized. (Thanks to David to let me know).
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, when winhttp.dll was dynamically loaded, after call WriteData method, an error 87 (Invalid Parameter) was returned.
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, internal Handle was not cleared. (Thanks to David to let me know).
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, if Asynchronous was enabled, connection was not initialized properly.
 [*] : Fixed Bug TsgcWebSocketClient_WinHTTP, exception closing connection.
 [*] : Fixed Bug Installing sgcWebSockets for Lazarus on Linux, some units had invalid name (linux is case sensitive).
 [*] : Fixed Bug Installing sgcWebSockets for Lazarus on Linux, folder with Indy units had invalid name (linux is case sensitive).


## 4.3.7: 2020 May

 [+] : New Component TsgcTDLib_Telegram, Allows to build Telegram Clients using TDLib JSON library.
 [+] : New Demo "Telegram" which shows how connect to telegram API, send a Text message, receive text messages, available chats...
 [+] : Improved Kraken API Component, now WebSocket API supports private channels. Requires an API Key and API Secret from Kraken Account.
 [+] : Improved Kraken API Component, now REST API is supported (allows to create orders, cancel orders, get account information using HTTPs as protocol).
 [+] : Improved Kraken API Component, now HTTP requests can be stored in a log file.
 [+] : Updated Client Demo to show Kraken improvements.
 [+] : New Property "Intents" in Discord API Components, allow to filter which events are received (by default all).
 [+] : New Property TCPKeepAlive in TsgcWebSocketClient and TsgcWebSocketServer, allows to enable keep-alive on TCP socket level, to try to detect dropped connections (like cable unplugged).
 [+] : Improved events dispatch when notifyEvents = neAsynchronous to prevent errors (Requires Rad Studio 2010+).
 [+] : Improved Google Pub/Sub component, there are 3 new properties to customize local listening server (LocalIP, LocalPort, RedirectURL).

 [*] : Fixed Bug in TsgcWSAPI_Pusher, private and presence channel didn't work if OnPusherConnect event was not set. (Thanks to Ozzie to let me know).
 [*] : Fixed Bug compiling in Lazarus for Ubuntu, there was an error in Interfaced Component in JSON unit. (Thanks to Moctezuma to let me know).
 [*] : Fixed Bug Discord API, reconnecting after a disconnection from server, was not handled properly.
 [*] : Fixed Bug reading ALPNProtocol OnDisconnect event.
 [*] : Fixed Bug Access Violation on TsgcWebSocketClient calling method Connect and the server doesn't accept connection.
 [*] : Fixed Bug TsgcWebSocketClient sometimes return Active property True while it was already disconnected from server.
 [*] : Fixed Bug installing sgcWebSockets package on CBuilder 2010.
 [*] : Fixed Bug Protocol Clients, access violation when disconnecting in some cases.
 [*] : Fixed Bug Protocol Clients, trying to reconnect it may raise an access violation.
 [*] : Fixed Bug WebSocket Server + IOCP and destroying server, an exception was shown to user if there were active connections.
 [*] : Fixed Bug WebSocket Server + IOCP sometimes an exception "List index out of bounds" when disconnecting all active connections. (Thanks to Orhan to let me know).
 [*] : Fixed Bug TsgcWebSocketClient if watchdog executes in a secondary thread while client is destroying, an access violation appears. (Thanks to Dirk to let me know)
 [*] : Fixed Bug WAMP Server List Index out of bounds in some cases processing a Call Request.
 [*] : Fixed Bug WAMP Server Access Violation accessing an internal shared object.
 [*] : Fixed Bug Client Protocol Subscription events, don't use notifyEvents property of component and always dispatch events asynchronous.
 [*] : Fixed Bug Trials for CBuilder 10.2 and 10.3 a path was missing and package wasn't built.
 [*] : Fixed Bug HeartBeat.Timeout, depending on the Interval and Timeout values, connection was wrong closed.


## 4.3.6: 2020 April

 [+] : New Component TsgcHTTPGoogleCloud_PubSub_Client, Google Cloud Pub/Sub API provides messaging between applications and is designed to provide reliable, many-to-many, asynchronous messaging between applications.
 [+] : New Demo "Google/PubSub" which shows how connect to Google Cloud Pub/Sub API and create topics, subscriptions, publish messages, pull from queue...
 [+] : Improved Binance API Component, now allows to subscribe / unsubscribe channels when a connection is active.
 [+] : Improved Binance API Component, now user data stream is supported, requires an API Key to get: account, balance and orders updates.
 [+] : Improved Binance API Component, now REST API is supported (allows to create orders, cancel orders, get account information using HTTPs as protocol).
 [+] : Improved Binance API Component, now HTTP requests can be stored in a log file.
 [+] : Binance Demo has been updated to show changes.
 [+] : New Event Discord API component, OnDiscordResumed, is called after a session has been resumed.
 [+] : New Property WriteTimeOut in Server and Client Components.
 [+] : New Property LocalServerOptions.RedirectURL in OAuth2, allows to set a redirect url (example: http://localhost/oauth/)

 [*] : Fixed Bug MQTT 5.0 when ConnectProperties was enabled, connection was closed after connect.
 [*] : Fixed Bug SGC Client Protocol, potential thread-lock reading/writing socket data.
 [*] : Fixed Bug Dataset Client Protocol, potential thread-lock reading/writing socket data.
 [*] : Fixed Bug TsgcWebSocketClient when WatchDog try to reconnect, if there is an exception now is captured and raised OnException event.
 [*] : Fixed Bug HeartBeat Timeout, after first validation, thread was terminated and not works until reconnect.
 [*] : Fixed Bug OnUnknownAuthentication event was not published for TsgcWebSocketServer component.
 [*] : Fixed Bug TsgcWebSocketHTTPServer when IOCP is enabled, when server is stopped, if there are connections alive, an unhandled exception message was shown to user.
 [*] : Fixed Bug TsgcWebSocketServer / TsgcWebSocketHTTPServer, after calling TsgcWSConnection.Close method, thread connection enter in non-stop bucle.
 [*] : Fixed Bug SignalR API Component, if cannot connect to server, exception was not catched.

 [/] : Renamed methods from Binance API component: AddAggregateTrades --> SubscribeAggregateTrades, RemoveAggregateTrades --> UnSubscribeAggregateTrades...
 [/] : Renamed Property LocalServerOptions.Host property in OAuth2 component, now is LocalServerOptions.IP.



## 4.3.5: 2020 March

 [+] : New Component TsgcHTTPAWS_SQS_Client, Amazon SQS is a fully managed message queues for microservices, distributed systems, and serverless applications.
 [+] : New Component TsgcWSAPI_Discord, Discord is one of the most popular communication tools for online gaming and streaming. (Thanks to Adriaan for his help).
 [+] : New Demo "Amazon/SQS" which shows how connect to Amazon SQS service and create queues, send and receive messages, get queues...
 [+] : Updated Client Demo to show how Discord Gateway API works.
 [+] : New Property in Socket.IO API "EncodeParameters", if enabled, encode url parameters of http get session.
 [+] : New event in WAMP 2.0 Protocol, OnWAMPChallenge: when server requires authentication, in this event "secret key" can be set.
 [+] : Updated URL property of TsgcWebSocketClient, now accepts "tcp" connections, so you can pass a url like this: "tcp://127.0.0.1", so will use TCP instead of websocket as protocol.
 [+] : New FMXMQTT demo which shows how MQTT client works in FMX (windows, mac os, linux64...)
 [+] : New SignalR demo showing how connect to c# signalr server.
 [+] : Improved internal HTTPs calls for APIs and Protocols clients, now https requests take the same properties than TLSOptions of TsgcWebSocketClient.

 [*] : Fixed Bug Snapshots demo, there was a memory leak creating image in web browser client side.
 [*] : Fixed Bug Published field 'CertStatus' not a class or interface type. (Thanks to Mark to let me know).
 [*] : Fixed Bug in OpenSSL 1.1.1 and iOS, cannot load library.
 [*] : Fixed Bug WAMP 2.0 Protocol, Subscribe method always send option parameter with default value, now Subscribe method has a new parameter called "Options".
 [*] : Fixed Bug compiling Indy Beta for Android 64.
 [*] : Fixed Bug WatchDog was not working for SignalR and SignalRCore APIs.
 [*] : Fixed Bug MQTT and plain TCP protocol, error parsing multiple messages (using websocket as protocol, worked well).
 [*] : Fixed Bug WebSocketServer with IOCP, if client disconnects with Options.CleanDisconnect = False, server doesn't fire OnDisconnect event.



## 4.3.4: 2020 February

 [+] : New Component TsgHTTP_OAuth2, this protocol allows third-party applications to grant limited access to an HTTP service, either on behalf of a resource owner or by allowing the third-party application to obtain access on its own behalf.
 [+] : New Property in TsgcWebSocketClient component, "Authentication.Token.OAuth" allows to link to a TsgcHTTP_OAuth2 and obtain an access token before websocket client connects to server.
 [+] : New Demo "OAuth2" which shows how connect to get OAuth2 credentials from Google API.
 [+] : New Event "OnSSLVerifyPeer" in TsgcWebSocketClient, allows to verify with more detail certificates.

 [*] : Fixed Bug in DoUnRegisterProtocol method, an Access Violation was raised calling it. (Thanks to Alessandro to let me know).
 [*] : Fixed Bug in OpenSSL 1.1.1 when VerifyCertificate was enabled. (Thanks to Mathieu to let me know).



## 4.3.3: 2020 January

 [+] : Added support for IOCP Indy Server (Websocket and HTTP Servers). There is a new property called IOHandlerOptions where you can select which IOHandler user (indy default or IOCP for Windows). *Requires custom Indy version (Beta).
 [+] : Updated Trial for Lazarus to version Lazarus 2.0.6.

 [*] : Fixed Bug Client Component, when receives a Close Frame, sometimes memory becomes corrupted (Thanks to Michael to let me know).



## 4.3.2: 2019 December

 [+] : Added support for Android 64bits in Rad Studio 10.3.3 Rio.
 [+] : Added support for OpenSSL 1.1.1 for Indy based components. *Requires custom Indy version (Beta)
 [+] : New Event OnSSLALPNSelect in TsgcWebSocketServer and TsgcWebSocketServerHTTP. *Requires custom Indy version (Beta)
 [+] : Added Support for ALPN (Application-Layer Protocol Negotiation) for Server and Client components based on Indy. *Requires custom Indy version (Beta)
 [+] : New Property "Port" in TsgcIoTAmazon_MQTT_Client, by default uses port 8883. If port is 443, uses ALPN automatically to connect. *Requires custom Indy version (Beta)
 [+] : New Property "ECDHE" in OpenSSL_Options of Server component, allows to fix chrome warning when using RSA with TLS 1.2
 [+] : Updated Demo Chat to show the use of OpenSSL API 1.0 and 1.1.

 [*] : Fixed Bug compiling XE8 package for OSX.
 [*] : Fixed Bug SGC Protocol, when server publish a message in a channel with qosLevel1 or qosLevel2, message never was sent to client.



## 4.3.1: 2019 October

 [+] : Added support for MQTT 5.0.
 [+] : Added support for HTTP Server API in CBuilder.
 [+] : Added support for TsgcWebSocketClient_WinHTTP in CBuilder.
 [+] : Added support for SChannel in CBuilder.
 [+] : New property Authorization Token for TsgcWebSocketClient, Bearer Tokens are now supported by websocket client.
 [+] : By default, when component request HMACSHA256 uses openssl libraries. Now, for Delphi 10 or greater, if there is no openssl library, uses System.Hash unit to calculate hash. (Thanks to Dirk to let me know)

 [*] : Fixed Bug MQTT Protocol, when a binary packet contains more than one mqtt message, only first message was processed.
 [*] : Fixed Bug MQTT Protocol sending UTF8 characters of length > 1.
 [*] : Fixed Bug MQTT Protocol, when using plain TCP connections, sometimes packets were not read properly.
 [*] : Fixed Bug when installing library in Rad Studio (Delphi and CBuilder), CBuilder projects raise linking errors.
 [*] : Fixed Bug in TsgcWebSocketClient if SChannel selected. When client disconnects, exception object was corrupted if Asynchronous property was selected.
 [*] : Fixed Bug in TsgcWebsocketServer_HTTPAPI, access violation trying to access to IP property value.
 [*] : Fixed Bug in TsgcWebsocketServer_HTTPAPI, OnShutdown event was not called after calling Active := False.
 [*] : Fixed Bug in Server Broker Component, when it was attached to a server but connection uses other subprotocol, all messages were encapsulated in broker protocol.
 [*] : Fixed Bug in SignalR API, when trying to negotiate connection, if ConnectionTimeout property wasn't returned by server, client raises an error and doesn't continue negotiation.

 [/] : Now HTTP Server API is compiled using dynamic linking, compile using "SGC_HTTPAPI_STATIC" if you need static linking (CBuilder only supports dynamic linking).
 [/] : Now TsgcWebSocketClient_WinHTTP is compiled using dynamic linking, compile using "SGC_WINHTTP_STATIC" if you need static linking (CBuilder only supports dynamic linking).
 [/] : Now SChannel is compiled using dynamic linking, compile using "SGC_SCHANNEL_STATIC" if you need static linking (CBuilder only supports dynamic linking).
 [/] : MQTT OnConnect event, ReturnCode now is an Integer. Has 2 new parameters: ReturnReason and ConnectProperties.
 [/] : MQTT OnSubscribe event, TsgcWSSUBACK from aCodes parameter, QoS --> ReturnCode, Result --> ReturnReason. Has a new parameter: SubscribeProperties.
 [/] : MQTT OnUnsubscribe event, has 2 new parameters: Codes and UnsubscribeProperties.
 [/] : MQTT OnPublish event, has 1 new parameter: PublishProperties.
 [/] : MQTT OnPubACK event, has 3 new parameters: ReasonCode, ReasonName and PubAckProperties.
 [/] : MQTT OnPubRec event, has 3 new parameters: ReasonCode, ReasonName and PubRecProperties.
 [/] : MQTT OnPubComp event, has 3 new parameters: ReasonCode, ReasonName and PubCompProperties.
 [/] : MQTT OnDisconnect event, has 3 new parameters: ReasonCode, ReasonName and DisconnectProperties.



## 4.3.0: 2019 September

 [+] : Added support for OSX64 in Delphi 10.3.2
 [+] : New Client API TsgcWSAPI_KRAKEN, is a US-based cryptocurrency exchange.
 [+] : Added Support for Authentication using Tokens in SignalRCore API. Client demo has been updated to show how works.
 [+] : New Event OnUnknownAuthorization in TsgcWebSocketServer and TsgcWebSocketServerHTTP. Allows to handle authorization requests like bearer tokens.
 [+] : Added support for TLS 1.3 when SChannel is selected.
 [+] : New event, OnHTTPRequest in TsgcWSAPI_SocketIO, allows to add custom headers to HTTP request to get session id.
 [+] : New Property Parameters in TsgcWSAPI_SocketIO, allows to set connection parameters.
 [+] : Improved TsgcWSAPI_SocketIO, if server sets pingInterval greater than zero and HeartBeat is not enabled, now HeatBeat is enabled automatically using server parameters.
 [+] : New Property "IOHandler" in TsgcIoTAmazon_MQTT_Client and TsgcIoTAzure_MQTT_Client, allows to select OpenSSL or SChannel.
 [+] : ThreadPoolSize of TsgcWebsocketServer_HTTPAPI now can be greater than 64.
 [+] : Improved speed detecting if protocol is registered when broker component is attached.
 [+] : Improved speed reading JSON Message in Server Protocols, some unneeded locks have been removed.
 [+] : New field QueryParams in THttpServerRequest of HTTP API Server.
 [+] : New field Cookies in THttpServerRequest of HTTP API Server.
 [+] : New Event OnCommandRequest on TsgcWSServer_HTTPAPI_WebBrokerBridge component, when server gets a new http request, this event is called and here you can customize http response.

 [*] : Fixed Bug allocating an unnecessary array when creating a new TsgcWSConnection.
 [*] : Fixed Bug in TsgcWebsocketServer_HTTPAPI, there was a memory leak destroying HTTP connection.
 [*] : Fixed Bug TsgcWebSocketHTTPServer if client connection uses HTTP 0.9/1.0, connection thread never ends and increase cpu load (Thanks to Boris to let me know).
 [*] : Fixed Bug SGC Server Protocol, if PubRel message does not exists, discard message and inform to client.
 [*] : Fixed Bug, if SetAuthenticationCloseCode was called, close code was not sent if Options.CleanDisconnect = False;
 [*] : Fixed Bug compiling Lazarus for Linux, sgcWebSockets_Resources.ppu file not compatible.
 [*] : Fixed Bug sgcWebSocket_Server_WebBrokerBridge unit reference to a incorrect indy unit.
 [*] : Fixed Bug SignalRCore API, ConnectionId was not assigned properly and left empty.
 [*] : Fixed Bug SignalRCore API, if TLS was selected, TLSVersion from websocket client was not used for HTTPs connections and always use default version.
 [*] : Fixed Bug SocketIO API, if no active internet connection, exception was not catched.
 [*] : Fixed Bug Server Protocol Components, when server has high load, sometimes parameters as reference become corrupted.
 [*] : Fixed Bug Client Protocols when calling from different threads, json messages were corrupted.
 [*] : Fixed Bug Client SGC Protocol, acknowledgment with qosLevel2 were not processed.
 [*] : Fixed Bug Dataset Protocol, synchronize method was not processed if ApplyUpdates = False.
 [*] : Fixed Bug TsgcWSServer_HTTPAPI_WebBrokerBridge, if url has parameters, webpage was redirected to default page.
 [*] : Fixed Bug TsgcWebsocketServer_HTTPAPI, request didn't set any value in Headers parameter.
 [*] : Fixed Bug Reading Bytes with Indy components, reading large amount of bytes, sometimes socket hangs.
 [*] : Fixed Bug reading fragmented messages.

 [/] : TsgcNotifyObject renamed to TsgcWSNotifyObject
 [/] : TsgcObjectList renamed to TsgcWSObjectList
 [/] : Request object of TsgcWebsocketServer_HTTPAPI, now has QueryParams, Document now doesn't includes query parameters.


## 4.2.6: 2019 June

 [+] : Added SChannel support for WebSocket Client.
 [+] : New Property CertStoreName in TsgcWebsocketServer_HTTPAPI, allows to set the name of certificate store where is certificate.
 [+] : New properties in SSLOptions in TsgcWebSocketServer, allows to set TLS Version and VerifyCertificate.
 [+] : MQTT Client now accepts Client Identifiers with more than 23 characters.
 [+] : Update Client Demo to show how connect to AWS AppSync.
 [+] : New Property UserAgent in SocketIO API.

 [*] : Improved speed TsgcWebsocketServer_HTTPAPI, when connection doesn't requiere authorization.
 [*] : Fixed Bug Server SGC Protocol, error reading broker message, when TsgcWebSocketServer_HTTPAPI is attached.
 [*] : Fixed Bug Server File Protocol, error reading broker message, when TsgcWebSocketServer_HTTPAPI is attached.
 [*] : Fixed Bug Server Presence Protocol, error reading broker message, when TsgcWebSocketServer_HTTPAPI is attached.
 [*] : Fixed Memory Leak Presence Protocol (Server and Client), TsgcWSAckMessages were created and not destroyed.
 [*] : Fixed Bug compiling Lazarus for Linux, sgcWebSockets_Resources file is not found.
 [*] : Fixed Bug compiling Lazarus for Linux, sgcResources.res file is not found.
 [*] : Fixed Bug compiling Lazarus for Linux, Abstract methods cannot be called directly in sgcWebSocket_Server_Base.LockList method
 [*] : Fixed Bug connecting to a server behind CloudFlare proxy.


## 4.2.5: 2019 May

 [+] : New Event AfterConnect in TsgcWSAPI_SocketIO, this event is called after socket.io connection is successful and client can send messages to server.
 [+] : New Property Socket.IO Polling in TsgcWSAPI_SocketIO, disabling this property, client will connect directly to server using websocket as transport.
 [+] : Updated Bitstamp API to version 2.
 [+] : New Event OnCommandRequest on TsgcWSHTTPWebBrokerBridgeServer component, when server gets a new http request, this event is called and here you can customize http response.
 [+] : New Property ClearReceivedStreamsOnDisconnect on Files Protocol, if disabled, when reconnects, try to resume file download for qosLevel2.
 [+] : New Property ClearSentStreamsOnDisconnect on Files Protocol, if disabled, when reconnects, try to resume file upload for qosLevel2.
 [+] : New Property TCPEndOfFrameScanBuffer in TsgcWSConnection class, allows to define which method use to find end of message.
	eofScanNone: every time a new packet arrive, OnBinary event is called.
	eofScanLatestBytes: if latest bytes are equal to bytes added with AddTCPEndOfFrame method, OnBinary message is called, otherwise this packet is buffered
	eofScanAllBytes: search in all packet if find bytes equal to bytes added with AddTCPEndOfFrame method. If true, OnBinary message is called, otherwise this packet is buffered
 [+] : New Method AddTCPEndOfFrame in TsgcWSConnection class, if connection is plain TCP, allows to set which byte/s define the end of message. Message is buffered till is received completely.
 [+] : Updated File Protocol, now SendFile/BroadcastFile accepts FileId as parameter, if FileId is blank, will work as before, value will be assigned automatically.

 [*] : Fixed Bug Server Protocol searching channel subscriptions when channel is empty.
 [*] : Fixed Bug WriteAndWaitData method, doesn't wait in Android and iOS.
 [*] : Fixed Bug Ping with Timeout, doesn't wait in Android and iOS.
 [*] : Fixed Bug Connect method for client component, doesn't wait in Android and iOS.
 [*] : Fixed Bug Disconnect method for client component, doesn't wait in Android and iOS.
 [*] : Fixed Bug Internal Timer for QoS Level2, doesn't work after a reconnect.
 [*] : Fixed Bug Socket.IO client, if Heartbeat enabled and timeout > 0, connection always disconnect after timeout.
 [*] : Fixed Bug Server File Protocol, property files doesn't read assigned values and always use default.
 [*] : Fixed Bug File Protocol, if sending a file using qosLevel2, there was a disconnection, after reconnect, process won't continue.
 [*] : Fixed Bug MQTT Protocol decoding QoS for Publish messages.
 [*] : Fixed Bug MQTT Protocol reading Packet Identifier for Publish messages.
 [*] : Fixed Bug MQTT Protocol writing Packet Identifier when was greater than 255.
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, when a client send a POST method, content property was empty.
 [*] : Fixed Bug Detecting HTTP POST Header when version is 1.0.
 [*] : Fixed Bug Detecting WebSocket Header when client sends a POST with websocket headers.
 [*] : Fixed Bug during HTTP negotiation for BITTREX Component, now requires TLS 1.2 to connect to server.
 [*] : Fixed Bug SignalR API component, now HTTP negotiation takes TLS version from TLSOptions of TsgcWebSocketClient component.
 [*] : Fixed Bug CBuilder reading CleanDisconnect property, now this property is public instead of published for CBuilder.
 [*] : Fixed Bug File Server Protocol calling BroadcastFile method (abstract error) when HTTP API Server is attached.
 [*] : Fixed Bug File Server Protocol, list index out of bounds processing acknowledgment.



## 4.2.4: 2019 April

 [+] : New Component "TsgcIoTAzure_MQTT_Client", MQTT client to connect to Azure IoT Server Broker.
 [+] : New Client API TsgcWSAPI_FXCM, is a retail broker for trading on the foreign exchange market.
 [+] : New property TLSOptions in TsgcWebSocketClient, allows to set Certificates filenames, certificate password and TLS Version.
 [+] : Updated WebBrokerBridge demo to enable SSL connections.

 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, Disconnect event was called for HTTP requests.
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, Disconnect event was not called for connections being abruptly closed.
 [*] : Fixed Bug TsgcWS_API_SocketIO, namespace was not registered when client connect to socket.io server.


## 4.2.3: 2019 March

 [+] : New Component "TsgcIoTAmazon_MQTT_Client", MQTT client to connect to Amazon AWS IoT Server Broker.
 [+] : New Method "Connect" TsgcWebSocketClient, try to connect to the server and wait till the connection is successful.
 [+] : New Method "Disconnect" TsgcWebSocketClient, try to disconnect from the server and wait till disconnection is successful.
 [+] : New method "Invite" Client Presence protocol, allows sending an invitation to another member to subscribe to a channel.
 [+] : If TsgcWebSocketClient.Options.CleanDisconnect = True, when set Active := False, client sends a message to the server to close connection.
 [+] : New Property in HTTP API Server, Asynchronous, if enabled, messages are sent asynchronously, by default is disabled so waits till a message is sent to client.
 [+] : New Event in HTTP API Server, OnAsynchronous, this event is called after an asynchronous completion call.

 [*] : Fixed Bug TsgcWebsocketServer_HTTPAPI, if there was an error sending heartbeat to a client, the process not continue with the next client.
 [*] : Fixed Bug TsgcWebSocketServer_HTTPAPI, SSLHash was not set in NewBinding method.
 [*] : Fixed Bug TsgcWebsocketServer_HTTPAPI, GetURL was not implemented.
 [*] : Fixed Bug TsgcWebsocketServer_HTTPAPI, if connections are free delayed, when a protocols was attached, connection was not added to queue.
 [*] : Fixed Memory Leak in TsgcWebSocketServer_HTTPAPI server component.
 [*] : Fixed Bug STOMP Protocol when NotifyEvents = neNosync, events where not called.


## 4.2.2: 2019 February

 [+] : Added support for SignalRCore, new client component TsgcWSAPI_SignalRCore, is an open-source library that simplifies adding real-time web functionality to apps.
 [+] : Updated Client demo for SignalRCore.
 [+] : Updated HTTPAPI Server demo.
 [+] : Improved Help manual, shows how install sgcWebSockets package step by step and most common errors.

 [*] : Fixed Bug TsgcWebSocketServer if Basic Authorization was enabled, connection thread never ends and increase cpu load.
 [*] : Fixed Bug TsgcWebSocketServer when custom headers are sent on handshake, in some cases may close connection.


## 4.2.1: 2019 January

 [+] : Subscribe/Unsubscribe methods from Protocol Components, now accepts multiple channels. Just send channels separated by commas, to subscribe/unsubscribe from multiple channels.

 [*] : Improved speed calling method WriteQueueData.
 [*] : Improved speed calling to save session id when using authentication.
 [*] : Improved speed saving MethodId in SGC Server Protocol.
 [*] : Improved speed writing data in SGC Server Protocol.
 [*] : Improved speed writing data in Files Server Protocol.
 [*] : Improved speed writing data in Dataset Server Protocol.
 [*] : Improved speed server detecting authentication type.
 [*] : Improved speed decoding websocket headers.
 [*] : Improved speed subscribe/unsubscribe to channels.
 [*] : Improved speed extension permessage-deflate.
 [*] : Fixed Bug TsgcWebSocketServer using plain TCP connections, OnBinary event was not called.
 [*] : Fixed Bug using plain TCP connections, OnConnect event was not called.
 [*] : Fixed Bug when notifyEvents = neAsynchronous, in some circumstances, index out of list processing asynchronous events.
 [*] : Fixed Bug LoadBalancer Client can't connect to LoadBalancer server if TLS is enabled.
 [*] : Fixed Bug SGC Protocol, when no channel is passed in publish method, exclude/include parameters may fail.
 [*] : Fixed Bug TsgcWebSocketServer when heartbeat is enabled, if new connection is created after last broadcasted ping and before heartbeat timeout, connection was closed by error.
 [*] : Fixed Bug MQTT Range Check Error.
 [*] : Fixed Bug Broker Component, if OnError event is fired with "connection has been gracefully closed", OnDisconnect event is not called and watchdog doesn't works properly.
 [*] : Fixed Bug Server Authentication, Authenticated variable was not initialized before OnAuthentication event.
 [*] : Fixed Bug TsgcWSConnection.Close method, doesn't works properly.
 [*] : Fixed Bug Validating UTF8 strings.
 [*] : Fixed Bug reading extension permessage-deflate.
 [*] : Fixed Bug websocket client, dead-lock accessing internal read thread.

 [/] : TsgcThreadList class moved to sgcWebSocket_Classes_SyncObjs
 [/] : TsgcCriticalSection class moved to sgcWebSocket_Classes_SyncObjs


## 4.2.0: 2018 December

 [+] : Added support for Rad Studio 10.3 Rio.
 [+] : New Protocol Presence (Server and Client), allows to know who is subscribed to a channel, example: chat rooms, collaborators on a document, people viewing the same web page, competitors in a game...
 [+] : New Client Component TsgcWSAPI_Bitmex, is a cryptocurrency exchange and derivative trading platform.
 [+] : New Server Event, OnUnknownProtocol, if protocol is not detected, here you can set which protocol use (example: allows to set plain TCP protocol).
 [+] : New Presence Demo which shows how Presence protocol works.
 [+] : New AppRTCEmbed demo, uses CEF4Delphi library to embed Chromium-based browsers in a client application to use AppRTC online demo without any webbrowser installed. More infor about CEF4Delphi: https://github.com/salvadordf/CEF4Delphi



## 4.1.11: 2018 November

 [+] : MQTT Protocol now support publishing binary data.
 [+] : New demo called "Mobile" replace "iOS" demo and shows how connect to a secure WebSocket server in Android 7.0+.
 [+] : New Property in HTTP API Server, Timeouts, allows to override default timeouts of HTTP API Server.
 [+] : New Property in HTTP API Server, ThreadPoolSize, by default 32 (maximum allowed is 64), allows to set number of threads of HTTP API Server.
 [+] : New Property in HTTP API Server, MaxBandwidth, maximum allowed bandwidth rate in bytes per second (zero means unlimited, value by default).
 [+] : New Property in HTTP API Server, MaxConnections, maximum number of connections (zero means unlimited, value by default).

 [*] : Fixed Bug AppRTC Protocol, when close call and try to rejoin shows an error.
 [*] : Fixed Memory Leak in MQTT Protocol component when destroying object.
 [*] : Fixed Bug MQTT Protocol, Packet Identifier was not read properly and if QoS = "At least once" or "Exactly once" messages could be sent duplicated.
 [*] : Fixed Bug MQTT client, after reconnect queued messages where not published.
 [*] : Fixed Memory Leak in STOMP Protocol component when destroying object.
 [*] : Fixed Error compiling in Lazarus for Linux with unit sgcWebSocket_Resources, unit name was incorrect.
 [*] : Fixed Bug HTTP API Server, when adding new binding with a parameter, this was not read properly in some cases.
 [*] : Fixed Bug HTTP API Server, size of payload message was not calculated properly.
 [*] : Fixed Bug HTTP API Server, only one thread was created to handle client connections.
 [*] : Fixed Bug HTTP API Server, disconnect event was not called in some cases.
 [*] : Fixed Memory Leak in HTTP API Server, internal heartbeat timers were not destroyed.
 [*] : Fixed some minor Bugs HTTP API Server.
 [*] : Fixed Bug in QueueLevel properties, if there is a disconnection before all queues are processed a memory leak can occur.
 [*] : Fixed Bug using Queues, in some cases stream was not saved properly.
 [*] : Fixed Bug LoadBalancer calculating server client connections count.
 [*] : Fixed Bug error "invalid pointer", notifying subscription/unsubscription when notifyEvents = neAsynchronous.



## 4.1.10: 2018 October

 [+] : New Client Component TsgcWSAPI_Cex,  is a cryptocurrency exchange and former Bitcoin cloud mining provider.
 [+] : New WebSocket Server Protocol: AppRTC, is a WebRTC server using AppRTC Demo code.
 [+] : New Demo for AppRTC protocol.

 [*] : Fixed Bug when calling disconnect, some methods where called more than once.
 [*] : Fixed Bug TThread calling terminate before Execute method has been called.
 [*] : Fixed Bug OnException event, sometimes Exception parameter was corrupted.
 [*] : Fixed Bug WebRTC protocol, remote video was not working.
 [*] : Fixed some stability issues in websocket client component in high load connections.
 [*] : Fixed Bug File Protocol when call WriteData method. 
 [*] : Fixed Bug File Protocol when Files.BufferSize = 0 and Files.QoS.Level = qosLevel1 or qosLevel2, when a file was sent never end.
 [*] : Fixed Bug List Index Out of Bounds in some cases when trying to access to Channels Subscribed.

 [/] : Properties RecBytes and SendBytes of TsgcWSConnection now are Int64.
 [/] : WebRTC protocol, now remote video is assigned in sgcaddstream event.



## 4.1.9: 2018 September

 [+] : New Server TsgcWSHTTPWebBrokerBridgeServer, which allows combine HTTP, DataSnap and WebSocket requests using the same server and port.
 [+] : New Client Component TsgcWSAPI_Huobi, is an international multi-language cryptocurrency exchange
 [+] : New Demo WebBrokerBridge, shows a simple datasnap and websocket server.
 [+] : New Demo AndroidService, shows how a websocket client can run as Android service and show a notification every time receives a message.
 [+] : Added Pusher Tab in Client Demo.
 [+] : New Method WriteAndWaitData in TsgcWSConnection, sends a message and waits response from other peer.
 [+] : OnException event now provides original exception if exists.
 [+] : Added support for authentication methods TsgcWebSocketServer_HTTPAPI Server.
 [+] : New Event OnHTTPRequest in TsgcWebSocketServer_HTTPAPI server component, now server can handle websocket and HTTP connections.
 [+] : New Property Port in TsgcWebSocketServer_HTTPAPI server component, allows to set default listening port.


 [*] : Fixed Bug OnWatchdog event, when client starts in a thread method, reconnection now uses thread method too.
 [*] : Fixed Bug SGC Protocol error "list index out of bounds" calling publish method in some scenarios.
 [*] : Fixed Bug in client demo, STOMP was not well linked to MQTT when server was changed.
 [*] : Fixed Bug HTTP API Server, binary messages were not received properly.
 [*] : Fixed Bug HTTP API Server, authentication methods (URL and Basic) didn't work
 [*] : Fixed Bug Client when disconnecting from a thread.
 [*] : Fixed Bug STOMP protocol, content-length header was incorrect if message contains special characters.
 [*] : Fixed Bug WatchDog was not working when Authentication Basic was used behind a Broker Protocol.
 [*] : Fixed Bug Client WebSocket Component, TsgcWSConnection.Free could be called more than once.
 [*] : Fixed Line Break Bug in Compiled HTML Help file.
 [*] : Fixed Bug Broadcasting streams when permessage-deflate compression is enabled.

 [/] : Property RegisteredURLs in TsgcWebSocketServer_HTTPAPI now is Bindings.


## 4.1.8: 2018 June

 [+] : New Client Component TsgcWSAPI_Binance, is an international multi-language cryptocurrency exchange
 [+] : New Client Component TsgcWSAPI_SocketIO, replaces TsgcWebSocketClient_SocketIO (will be deprecated on future versions).
 [+] : New Client Component TsgcWSAPI_Bitstamp, Bitstamp is one of the world's longest standing crypto exchange, supporting the blockchain ecosystem since 2011.
 [+] : If there is an error connecting to a WebSocket server, now HTTP error code is showed in OnError event.

 [*] : Fixed Bug CBuilder 10.2.3 in static link library for Indy "inline __fastcall TIdEncoderMIME(System::Classes::TComponent* AOwner)..."
 [*] : Fixed Bug Pusher Protocol error "invalid path error" when connect to server.



## 4.1.7: 2018 May

 [+] : New Client Component TsgcWSAPI_SignalR, is a library for ASP.NET developers that makes developing real-time web functionality using websockets as transport.
 [+] : New Client Component TsgcWSAPI_Bittrex, is a US-based cryptocurrency exchange.
 [+] : New Property "CloseReason" in TsgcWSConnection, is reason why connection has been closed by other peer.
 [+] : Poloniex Demo improved, added api2.poloniex.com server.

 [*] : Fixed Bug when disconnect has a Close Reason, error code wasn't readed properly.
 [*] : Fixed Bugs compiling Delphi7 with latest Indy version.
 [*] : Fixed Bug in sgcWebSocket_HTTPAPI, ULONGLONG was redeclared.
 [*] : Fixed Bug in design package dclsgcWebSocketsD*.* only win32 personality is needed.
 [*] : Fixed Bug Dataset Protocol if UpdateMode = upWhereChanged, only key fields were updated.
 [*] : Fixed Bug Deleting TsgcPing elements from server/client components.
 [*] : Fixed Bug compiling for Delphi2006 with latest Indy version.
 [*] : Fixed WebRTC warnings.



## 4.1.6: 2018 March

 [+] : New Component TsgcWSPClient_STOMP, generic STOMP Protocol client, allows to connect to any STOMP Server
 [+] : New Component TsgcWSPClient_STOMP_RabbitMQ, STOMP client for RabbitMQ Broker.
 [+] : New Component TsgcWSPClient_STOMP_ActiveMQ, STOMP client for ActiveMQ Broker.
 [+] : New Demo "Client" which shows how connect to: WebSocket Server, MQTT Server and STOMP Server.
 [+] : SGC Protocol Server, Publish method now is overloaded, new method now accepts QueueLevel (store last message or store all messages).
 [+] : SGC Protocol Server, Subscribe/UnSubscribe methods now supports wildcard characters, so you can subscribe to a hierarchy of channels. Example: if you want subscribe to all channels which start with 'news', then call Subscribe('news*').
 [+] : SGC Protocol Server, Publish method now supports wildcard characters, so you can publish to a hierarchy of channels. Example: if you want send a message to all subscribers to channels which start with 'news', then call Publish('news*').

 [*] : Fixed Bug Broker component processing messages when more than one protocol is attached.
 [*] : Fixed Bug BCBuilder compiling error in sgcWebSocket_WinAPI.
 [*] : Fixed Bug MQTT Client reading remaining length.
 [*] : Fixed Bug MQTT Client Heartbeat doesn't start after a disconnection.
 [*] : Fixed Bug Client when disconnecting from a thread.
 [*] : Fixed Bug TsgcPing in client component was not destroyed properly.
 [*] : Fixed Bug SGC Protocol method UnSubscribeAll was not destroying all subscriptions.
 [*] : Fixed Bug SGC Protocol if a message was published with queueLevel1, message was not retained in server.

 [/] : Property rename in TsgcWebSocketServer, Connections[Guid] now is ConnectionsByGuid[Guid]



## 4.1.5: 2018 February

 [+] : New Component TsgcWSAPI_Bitfinex, Bitfinex is one of the world's largest and most advanced cryptocurrency trading platform. Users can exchange Bitcoin, Ethereum, Ripple, EOS, Bitcoin Cash, Iota, NEO, Litecoin, Ethereum Classic...
 [+] : New Component TsgcWSAPI_Blockchain, Blockchain WebSocket API allows developers to receive Real-Time notifications about new transactions and blocks.
 [+] : New Component TsgcWSAPI_Pusher, Pusher is an easy and realiable platform with flexible pub/sub messaging, live user lists, authentication...
 [+] : New property "URL" in client components, read url and automatically set host, port, tls, parameters...
 [+] : New property "Parameters" in TsgcIWWebSocketClient, allows to set a parameter in url.

 [*] : Fixed Bug in Internet Explorer 8 using Flash as Fallback, error: "this.transport.indexOf" not supported.
 [*] : Fixed Bug WriteData as Text when RFC6455 Specification is False.
 [*] : Fixed Bug in ProtocolRegistered function when more than one protocol is supported by a single protocol.
 [*] : Fixed Bug "Constant expression violates subrange bounds" in sgcWebSocket_HTTPAPI_Server unit compiling for 64bits.
 [*] : Fixed Bug in sgcWebSockets.dll, error event was not raised if there was any error before a succesful connection.
 [*] : Fixed Bug ClientTest demo trying to connect to echo.websocket.org TLS
 [*] : Fixed Bug using sgcWebSocketLib.pas with Delphi 7.
 [*] : Fixed Bug RegisterProtocol with Broker component.
 [*] : Fixed Bug in TsgcWebSocketClient when WatchDog enabled and notifyEvents = neNoSync.


## 4.1.4: 2018 January

 [+] : Overloaded method to register subprotocols at runtime by name. Events are raised on Server/Client context in this case.
 [+] : Added New Methods in sgcWebSockets library to send binary messages using TBytes as parameter.
 [+] : Added support for Socket.IO API 2.*
 [+] : Updated Socket.IO to latest online demo.
 [+] : Added RegisteredURLs to TsgcWebSocketServer_HTTPAPI, allows to register which URLs will be handled by sgcWebSockets.

 [*] : Fixed Warnings compiling sgcWebSockets library with latest compiler.
 [*] : Fixed Bug compiling CBuilder with method SetPort.
 [*] : Fixed several bugs for TsgcWebSocketServer_HTTPAPI.



## 4.1.3: 2017 December

 [+] : New Component TsgcWebSocketServer_HTTPAPI (still Beta, not for production): Server based on Microsofot HTTP API 2.0 for windows and IOCP.
 [+] : Added New Property "UseNagle" for client and server websocket components (by default is enabled).
 [+] : Added 2 new units: sgcWebSocket_Protocol_Example_Server.pas and sgcWebSocket_Protocol_Example_Client.pas, to show how create custom subprotocols.
 [+] : Added 2 new methods: RegisterProtocol and UnRegisterProtocol, these methods allow attach protocols in run-time.

 [*] : Fixed Bug Uncaught ReferenceError: sgcWebSocket is not defined loading javascript file.
 [*] : Fixed Bug Dataset Protocol, decimals were truncated to 4, now there is no truncation.



## 4.1.2: 2017 October

 [+] : New Method WAMP 2.0 Protocol, InvocationError: when the callee is unable to process or finish the execution of the call.

 [*] : Fixed Bug WAMP 2.0 Protocol, yield method was not implemented.
 [*] : Fixed Bug WebRTC Demo, connection was not closed properly.
 [*] : Fixed Bug Protocol Base Message, in some cases could raise a Thread Lock.
 [*] : Fixed Bug Protocol Files, client didn't sent acknowledgment of file received.
 [*] : Fixed Bug Protocol Files, broadcast file using qosLevel1 was not working.



## 4.1.1: 2017 July

 [+] : New Protocol Component TsgcWSPClient_WAMP2, implements WAMP 2.0 protocol.
 [+] : Added support for Server Proxy Sub-Protocols.

 [*] : When connection is IPv6, built-in sgcWebSockets.html was not showed properly.
 [*] : Fixed Bug in TsgcWebSocketServerHTTP on Linux64, files inside DocumentRoot where not found.
 [*] : Fixed Bug in Delphi7, error compiling MQTT Client.
 [*] : Fixed Bug MQTT client, heartbeat only work if client enables it.
 [*] : Fixed Bug MQTT client, ClientIdentifier was ignored if CleanSession was true.
 [*] : Small fixes to allow Delphi7 compile latest Indy version.
 [*] : Fixed Bug MQTT client, dirty messages when subscribing with mtqsAtLeastOnce.
 [*] : Fixed Library Free version.
 [*] : Fixed Bug Dataset Protocol, LargeInteger was not properly decoded when Base64 was enabled.
 [*] : Fixed Bug if handshake message was fragmented, connection was closed.



## 4.1.0: 2017 April

 [+] : Added support for Rad Studio 10.2 Tokyo.
 [+] : Added support for Linux compiler.
 [+] : MQTT client, added subscribe method.
 [+] : MQTT client, added unsubscribe method.
 [+] : MQTT client, added publish method.
 [+] : MQTT client, added Authentication property, allows to set user and password to authenticate against MQTT Server.
 [+] : MQTT client, added HeartBeat property, keeps alive connection.
 [+] : MQTT client, added LastWillTestament property, when client disconnects, sends a message to other connected clients.
 [+] : New Property "NotifyDeletes" in Dataset Server Protocol, if enabled (by default) broadcast deleted record to all clients.
 [+] : New Method "BroadcastRecord" in Dataset Server Protocol, sends dataset record values to all clients.
 [+] : New Method "MetaData" in Dataset Server Protocol, sends metadata info to a single client.
 [+] : New Method "Synchronize" in Dataset Server Protocol, sends dataset record values to a single client.

 [*] : Fixed Bug ReadTimeout and ConnectionTimeout in client component.
 [*] : Added Guid property to Client File Protocol.
 [*] : Fixed Bug Invalid Character when trying to access to built-in javascript libraries.
 [*] : Fixed Bug File Protocol when BufferSize was set to zero, file was not saved properly.
 [*] : Fixed Memory Leaks on NextGen compiler.
 [*] : Fixed WebRTC Chrome console errors.



## 4.0.2: 2017 March

 [+] : New Component TsgcWSPClient_MQTT, implements MQTT protocol, it's still beta and next versions will support more methods.
 [+] : MQTT client, added connect method.
 [+] : MQTT client, added connack method.
 [+] : MQTT client, added pingreq method.
 [+] : MQTT client, added pingresp method.
 [+] : MQTT client, added disconnect method.

 [*] : Fixed Bug Javascript SGC Protocol, when calling rpc method with non numeric parameters.
 [*] : Fixed Access Violation on client components when hard socket disconnect.
 [*] : Fixed Bug Dataset Protocol, synchronization didn't search if record exists.
 [*] : Fixed Bug when client disconnects, sometimes OnDisconnect event was not raised.
 [*] : Fixed Bug Dataset Protocol, parsing error in float fields.


## 4.0.1: 2017 February

 [+] : WinHTTP client, added proxy support.
 [+] : WinHTTP client, added asynchronous request support.
 [+] : WinHTTP client, implemented query close status.

 [*] : Fixed Bug using OnBinary event in C#, added a new event to handle binary data using array of bytes.
 [*] : Fixed messages when compiling: unit '%s' implicitly imported into package '%s'
 [*] : Fixed Memory Leaks websocket server.
 [*] : Fixed Memory Leak TsgcWSClient.
 [*] : Fixed Bug, disconnect event was not raised in iOS / Android.
 [*] : Fixed Bug in WriteData method from protocol components.
 [*] : Fixed Bug, added QueueOptions to published properties of client.
 [*] : Fixed Bug, Access violation when Server.Active := False and SSL enabled.
 [*] : Fixed Bug, Access violation when Client.Active := False and SSL enabled.
 [*] : Fixed Bug, when RaiseDisconnectExceptions is not enabled, some exceptions were not catched.



## 4.0: 2017 January

 [+] : New Component TsgcWebSocketClient_WinHTTP based on WinHTTP API (requires Windows 8.1+)
 [+] : New Property "IpVersion" on Indy Client components: allows to set IPv4/IPv6 version.
 [+] : New Compiler Directive "SGC_WRITECONST": if enabled, allows to modify some of the constants like: authentication url, built-in libraries names, protocols...
 [+] : Added Delphi 2006 Package.

 [*] : Fixed Bug compiling iOS projects, access violations where raised and application hangs, when NotifyEvents where set to neAsynchronous.
 [*] : Fixed Bug WAMP Protocol parsing message type.
 [*] : Improved WAMP Protocol reading/writing messages.
 [*] : Fixed Bug WEBRTC Protocol calling "createOffer" method.
 [*] : Fixed BUG Socket.IO Client, using API 1.*, heartbeat was not handled.
 [*] : Fixed BUG CBuilder Multiple declaration for 'TsgcWSServer_Base::Connections'.
 [*] : Fixed BUG Socket.io client when TLS is enabled.
 [*] : Fixed Bug Client Component when WatchDog enabled and attempts > 0.
 [*] : Fixed Bug connection list was locked under certain circumstances.
 [*] : Fixed Bug HeartBeat was not working properly when Timeout > Interval.
 [*] : Fixed Bug ListIndex out of bounds on server protocol.
 [*] : Fixed Bug when server disconnects all connections.
 [*] : Fixed Bug Demo Tickets, dataset updates where not broadcasted.
 [*] : Fixed Bug Error decoding message, using Broker and GUID in protocols.
 [*] : Improved Reliability and Stability of Server.

 [/] : sgcJSON as Interface is only supported from Delphi 2010 to latest.
 [/] : Options.QueueText moved to QueueOptions.Text
 [/] : Options.QueueBinary moved to QueueOptions.Binary



## 3.5: 2016 May

 [+] : Added support for Rad Studio 10.1 Berlin.
 [+] : New Component LoadBalancerServer: allows to distribute client requests along several servers connected to a Load Balancer Server.
 [+] : New Event OnSSLGetHandler on Server / Client components: allows to create a custom SSL Handler based on IOHandlerSSLBase.
 [+] : New Event OnSSLAfterCreateHandler on Server / Client components: allows to customize default OpenSSL Handler.
 [+] : New Property "QueueText" on Server / Client components: if enabled (by default), text messages are added to a queue and are sent inside thread context.
 [+] : New Property "QueueBinary" on Server / Client components: if enabled, binary messages are added to a queue and are sent inside thread context.
 [+] : New Method "Start" on Server / Client components: starts in a secondary thread.
 [+] : New Method "Stop" on Server / Client components: stops in a secondary thread.
 [+] : New Method "Close": when called try to cleanly close a client connection from server side.
 [+] : New Method "CloseAll": closes cleanly all client connections.
 [+] : New Property "EncodeBase64" on Server / Client Dataset Protocol: if enabled, text fields are encoded/decoded automatically.
 [+] : New Property "IO_Namespace" on socket.io client component: if specified, sets namespace when connects to a Socket.IO server (+1.*)
 [+] : New Property "SOCKS" inside "Proxy" property: allows to use SOCKS proxies.
 [+] : Server Property "Connections" now accepts Guid as parameter.
 [+] : Added support for ftBlob fields in Dataset Protocol.

 [*] : Fixed Bug WAMP Protocol parsing custom JSON messages using Broadcast/writedata.
 [*] : Fixed Bug ListIndexError on Protocol Components.
 [*] : Fixed Bug Compiling Packages for RadStudio C++ XE8 and 10
 [*] : Fixed Bug Broker Components reading/writing messages
 [*] : Fixed Bug DeadLock in Server when a client losses connection.
 [*] : Fixed Bug ServerSentEvents sending Unicode Characters.
 [*] : Fixed Bug Disconnect event was not raised sometimes on client side.
 [*] : Fixed Bug JSON Parser.
 [*] : Fixed Bug SGC Protocol using notify method in javascript clients.
 [*] : Fixed Bug WebRTC Protocol.
 [*] : Fixed Bug WebRTC Protocol returns undefined onsgcmediaerror event.
 [*] : Fixed Bug FreePascal 3 opening handshake.
 [*] : Fixed Bug WebRTC Protocol using firefox.
 [*] : Fixed Bug Clearing Client Buffer OnException event.
 [*] : Fixed Bug IWClient, TLS forced 443 port.


## 3.4: 2015 September

 [+] : New Property "AutoEscapeText" on DataSet Protocol: disabled by default. Automatically escape/unescape characters inside field values like "{", "["...
 [+] : WriteData Method has a new parameter "size" which is the maximum size of every text packet. 
 [+] : New Property "ReadStartSSL" on HTTP Server component, max number of times an HTTPS connection tries to start.
 [+] : New Property "DisconnectAll" on Server components, disconnects all active connections.

 [*] : Fixed Bug Dataset Protocol sending/receiving messages.
 [*] : Fixed Bug re-sending messages using qosLevel2 through a broker.
 [*] : Fixed Bug when call to disconnect using ssl client connection.
 [*] : Fixed Bug when a client try to connect without handshake headers.
 [*] : Fixed Bug Files Protocol reading Message File.
 [*] : Fixed Bug Dataset Protocol sending updates from client.
 [*] : Fixed Bug Dataset Protocol raising dataset events.
 [*] : Fixed Bug Files Protocol QoSLevel2 for fragments not received.
 [*] : Fixed Bug Reading fragmented text message.
 [*] : Fixed Bug Reading SSE message from D2009+.
 [*] : Fixed Bug Reading/Writing using Protocols.
 [*] : Fixed Bug Client Component not clearing FWSConnection field when a connection was closed by server.
 [*] : Fixed Bug Client Component destroying Critical Section.
 [*] : Fixed Bug SGC Protocol OnDisconnect Event, an access violation was raised trying to send a message inside this event.


## 3.3: 2015 May

 [+] : Added support for Rad Studio XE8.
 [+] : New Property "RaiseDisconnectExceptions": enabled by default, raises an exception every time there is a disconnection by protocol error.
 [+] : New Property "IO_HandShakeCustomURL"on Socket.io client, overrides url to get socket.io session.
 [+] : New Event, "OnBeforeSubscription" on Server Component Protocols, allows/denies a client subscribe to a channel.
 [+] : New Property "FragmentedMessages", allows to handle Fragmented Messages:
           frgOnlyBuffer: message is buffered until all data is received, it raises OnBinary or OnMessage event (option by default)
           frgOnlyFragmented: every time a new fragment is received, it raises OnFragmented Event.
           frgAll: every time a new fragment is received, it raises OnFragmented Event with All data received from first packet. 
                   When all data is received, it raises OnBinary or OnMessage event.
 [+] : WriteData Method has a new parameter "size" which is the maximum size of every binary packet. 
 [+] : Added Support on Broker Protocol Components for binary messages.
 [+] : New Methods for SGC Client Protocol to retrieve Method and Parameters sent on RPC calls: GetRPCMethodById and GetRPCParamsById.
 [+] : Ping Method has been overloaded to accept a TimeOut, first sends a pings and waits a response, if no response after a timeout, returns false.
 [+] : New Property "Subscriptions" on Server and Client Protocol Components, returns a list of active subscriptions.
 [+] : New Event, "OnStartup" on WebSocket Servers, raised when a server is started.
 [+] : New Event, "OnShutdown" on WebSocket Servers, raised when a server is stopped.
 [+] : Method "Disconnect" of TsgcWSConnection now it's overloaded to accept close code as a parameter.
 [+] : New Method, SetAuthenticationCloseCode on TsgcWSConnectionServer, allows to set close code if not authenticated.
 [+] : Added support for broker on SGC Protocol using sgcWebSockets library.
 [+] : New Method "UnSubscribeAll" for Client SGC Protocol.

 [*] : Fixed Access Violation when Client tries to reconnect to Server.
 [*] : Fixed DeadLock when Client disconnects and buffer is not empty.
 [*] : Fixed Scape Error when JSON value is an object or array.
 [*] : Fixed Bug trying to disconnect a connection several times.
 [*] : Fixed Bug building CBuilder XE6-XE7 Package on Win64.
 [*] : Fixed Bug SGC Protocol OnMessage Event.
 [*] : Fixed Bug SGC Protocol WriteData Method.
 [*] : Fixed Bug SGC Protocol Broadcast Method.
 [*] : Fixed Bug Server Broadcast method using include / exclude arguments.
 [*] : Fixed Bug SGC Protocol using QoSLevel2.
 [*] : Fixed Bug SGC Protocol OnRPCResult Event, when result parameter was an array of objects.
 [*] : Fixed Bug SGC Dataset Client when attached to a broker.
 [*] : Fixed Bugs JSON parser.
 [*] : Fixed Bug HeartBeat Timeout.
 [*] : Fixed Bug Socket.IO Client on SendEvent method.
 [*] : Fixed Bug when using TsgcWSConnection.Data property OnDestroy Event.
 [*] : Fixed Bug DataSet Protocol when a DateTime Field IsNull.

 [/] : WriteData method now "Stream" parameter is a TStream.


## 3.2: 2014 September

 [+] : Added support for Rad Studio XE7.
 [+] : Added support for AppMethod.
 [+] : Added support for Server-Sent Events API (SSE), push notifications from server to client using http connection.
 [+] : Added suport for SSE on Javascript libraries: automatic fallback to SSE+XHR if WebSocket is not implemented.
 [+] : New Component TsgcWebSocketProxyServer: server that translates WebSocket protocol to normal socket, allowing a browser to connect to any application/server. 
 [+] : New Property "WatchDog"
           Server: keeps server active automatically (disabled by default).
           Client: reconnects automatically after an unexpected disconnection (disabled by default).
 [+] : New Property "LocalIP" on TsgcWSConnection, returns IP Address of Host.
 [+] : New Property "LocalPort" on TsgcWSConnection, returns Port Address of Host.
 [+] : New Property "HeartBeat" on Server Components: sends a ping every x seconds (disabled by default).
 [+] : New Property "IO_API" on TsgcWebSocketClient_SocketIO:
           ioAPI0: supports socket.io 0.* servers (selected by default)
           ioAPI1: supports socket.io 1.* servers 

 [*] : Fixed Bug writing data on TsgcWebSocketClient_SocketIO if connection is not Active.
 [*] : Fixed Bug on search paths runtime packages from Delphi XE3-XE6.
 [*] : Fixed DeadLock writing data on Server and Client components.
 [*] : Fixed Bug reading JSON objects passed as parameters in SGC and Dataset Protocols.
 [*] : Fixed Memory Leak OnException Event.
 [*] : Fixed Bug Broadcast method using Exclude parameter.
 [*] : Fixed Bug sending double quoted string inside a JSON parameter.
 [*] : Fixed DeadLock when Keep-Alive is active on TsgcWebSocketHTTPServer.
 [*] : Fixed Bug retrieving MIME-Type from file, when TsgcWebSocketHTTPServer tries to serve a file from DocumentRoot.
 [*] : Fixed DeadLock on TsgcTimer class when compiled as a library.
 [*] : Fixed Warnings.

 [/] : Deleted property TsgcWSConnectionServer.ServerHost
 [/] : Deleted property TsgcWSConnectionServer.ServerPort



## 3.1: 2014 May

 [+] : Added support for Rad Studio XE6.
 [+] : Added support for C++Builder (2010-XE6).
 [+] : Added support for old browsers (using Adobe Flash FallBack) without WebSocket implementation like Internet Explorer 6 to 9. 
 [+] : New WebSocket Extension: PerMessage-Deflate. Deflate-frame Extension has been deprecated and replaced by PerMessage-Deflate. 
 [+] : New Property "ReadTimeOut" on Server components, timeout to check if socket has received data.
 [+] : New Property "ReadEmptySource" on HTTP Server component, max number of times an HTTP connection is read with no data.
 [+] : New Property "Transport" on TsgcWSConnection, returns which transport is used (RFC6455, Hixie76, Flash or Undefinided).
 [+] : New Property "SessionList" on TsgcWebSocketHTTPServer.
 [+] : New Property "ParseParams" on TsgcWebSocketHTTPServer.

 [*] : Fixed Bug on DCP paths design packages from Delphi XE2-XE5.
 [*] : Fixed Bug reading if TCPConnection is connected.
 [*] : Fixed Bug detecting connection state on javascript library.
 [*] : Fixed Bug detecting type of message on javascript library.
 [*] : Fixed Bug setting client log filename.
 [*] : Fixed Bug sending a compressed close connection frame.



## 3.0: 2014 March

 [+] : New Library "sgcWebSockets.dll" which allows to handle WebSocket (Server and Client) connections from Delphi or C# .Net (Demos inside Library Folder)
	WebSocket Server
	WebSocket Client
	WebSocket SocketIO Client
	WebSocket Server Protocol SGC
	WebSocket Client Protocol SGC         
 [+] : New Property "IO_HandShakeTimestamp" on Socket.io client, if enabled allows to connect to gevent-socket.io servers

 [*] : Fixed Bug calculating SendBytes with Binary Messages.
 [*] : Fixed Bug TsgcWSConnection.WriteData when NotifyEvents = neNoSync.
 [*] : Fixed Bug assigning ssl properties after set active.
 [*] : Fixed Memory Leak in built-in libraries on some webbrowsers.
 [*] : Fixed Bug OnException Event on NEXTGEN compilers.
 [*] : Fixed Bug socket.io client on SendEvent procedure.
 [*] : Fixed Bug processing http cache requests.

 [/] : If you compile sgcWebSockets inside a DLL or a console application, there is no need to call CheckSynchronize manually.



## 2.6: 2013 November

 [+] : Added support for Rad Studio XE5
 [+] : Added support for Android
 [+] : Added Basic Authentication support for VCL Websockets and HTTP Requests.
 [+] : New for Protocols "sgc" and "Dataset": Added "Queue" param to the following methods: RPC, Publish and Notify:
         Level 0: messages are not queued on Server
         Level 1: last message is queued on Server, and is sent every time a client subscribes to a new channel or connects to server.
         Level 2: all messages are queued on Server, and is sent every time a client subscribes to a new channel or connects to server.
 [+] : New "QoS" Level (Quality of Service):
         Level 2: messages are assured to arrive exactly once. If the acknowledgement message is not received after a specified period of time, the message is sent again.
 [+] : New Property "Throttle": if enabled, limits the amount of bandwith usage.
 [+] : New Demo: Server Authentication
 [+] : Improved Documentation: new topics about features and general questions.

 [*] : Fixed Bug with TsgcWebSocketServer on Windows XP.
 [*] : Fixed Bug Connecting using a sub-protocol and using Authentication.
 [*] : Fixed Bug in TsgcWebSocketServer causing clients to hang on unauthorized connection.
 [*] : Fixed Bug in TsgcWebSocketHTPServer, http sessions were not created.



## 2.5: 2013 September

 [+] : Improved Socket.IO client with new methods and events.
 [+] : New Property "RawMessages" on Socket.IO client: if true, socket.io messages are not processed (it works as before 2.5 udpate); if false, it handles socket.io messages (false by default).
 [+] : New for Protocols "sgc" and "Dataset": Added Support for transactional messages through server local transactions. 
       When a client Starts a Transaction on a channel, all messages sent to this channel are queued until client do a commit.
 [+] : New for Protocols "sgc" and "Dataset": Added "QoS" (Quality of Service) property with 2 values:
         Level 0: messages are delivered according to the best efforts of the underlying TCP/IP network (active by default).
         Level 1: messages are assured to arrive but duplicates may occur. If the acknowledgement message is not received after a specified period of time, the message is sent again.
 [+] : New for Protocols "sgc" and "Dataset": Added event "OnSession", it raises when server sends client session id. 
       By default is sent by server after a client connection.
 [+] : New for Protocols "sgc" and "Dataset": Added Method GetSession. Allows to get server session id of connection.
 [+] : New for Client Protocols "sgc" and "Dataset": Added event "OnAcknowledgment", an acknowledgment is sent by server to client when receives a message from client.
 [+] : New for Server Protocol "Dataset": Added property "UpdateMode" [upWhereAll]: updates all fields of a record, [upWhereChanged]: updates only fields that have changed.
 [+] : New for Client Protocol "Dataset": Added Event "OnMetaData" to get field structure of server dataset.
 [+] : New for All Protocols: Added Event OnRawMessage , allows to handle protocol messages.
 [+] : New Property "ConnectTimeout" on Client Components.
 [+] : New Property "ReadTimeout" on Client Components.
 [+] : New Property "Queue", when "true" queues string/binary messages and when "false" process all messages.
 [+] : New Method "QueueClear", clear all queued messages.
 [+] : New Events on TsgcWSPServer_Dataset:
         + OnBeforeNewRecord
         + OnBeforeUpdateRecord
         + OnBeforeDeleteRecord
         + OnBeforeDatasetUpdate
         + OnAfterNewRecord
         + OnAfterUpdateRecord
         + OnAfterDeleteRecord
         + OnRPCAuthentication
         + OnNotification
         + OnRPC

         + OnRPCAuthentication
 [+] : New Events on TsgcWSPClient_Dataset:
         + OnBeforeNewRecord
         + OnBeforeUpdateRecord
         + OnBeforeDeleteRecord
         + OnBeforeDatasetUpdate
         + OnBeforeSynchronize
         + OnAfterSynchronize
         + OnRPCResult

         + OnRPCError
         + OnEvent
 [+] : Property HandShake now is public on TsgcWSConnectionServer class.
 [+] : Property Connection now is public on Client Component.
 [+] : Added Interfaces directory with source code interfaces.


 [*] : Fixed Bug sending Options.Parameters on SocketIO client.
 [*] : Fixed Bug Handling Error Event.
 [*] : Fixed Bug WAMP Server Protocol using publish method (messages were broadcasted to all clients, subscribed or not).
 [*] : Fixed Bug Broker Server Component (events were forwarded to protocol components).
 [*] : Fixed Bug WriteData Method if TCPConnection has been destroyed.
 [*] : Fixed Bug UnSupported Protocol raised an access violation
 [*] : Fixed Bug WAMP Server Protocol, now CallId is unique by client connection.
 [*] : Fixed Bug getting IP from TsgcWSConnection.
 [*] : Fixed Bug calling Synchronize Method first time on Protocol Dataset Client.
 [*] : Fixed Bug Reading JSON Boolean values.
 [*] : Fixed Bug Serving DocumentRoot files.
 [*] : Fixed Memory Leak on Server Component.

 [/] : OnConnectionData event has been removed. Now Connection.Data is read/write.
 [/] : OnAfterNewRecord event Added Connection as Parameter.
 [/] : OnAfterUpdateRecord event Added Connection as Parameter.
 [/] : OnAfterDeleteRecord event Added Connection as Parameter.



## 2.4: 2013 June

 [+] : Added support for Rad Studio XE4
 [+] : Added support for NEXTGEN IOS Compiler
 [+] : New Method "Disconnect": allows to disconnect a client connection from server side.
 [+] : New Property "LogFile" (Server and Client components): save messages to a log file, useful for debugging.
 [+] : Improved "Protocol DataSet": now synchronizes in Two ways (from server to client and from client to Server).
 [+] : New Property "AutoSynchronize" (Protocol Dataset Server): synchronizes automatically all records OnConnect event.
 [+] : New Method "Synchronize" (Protocol Dataset Client): synchronizes automatically all records from Server.
 [+] : New Property "NotifyUpdates" (Protocol Dataset): allows to notify updates from server to client or client to server.
 [+] : New Property "ApplyUpdates" (Protocol Dataset): allows to apply updates from server to client or client to server.
 [+] : New Property "AllowNonAuth": allows to connect to non-authenticated users if authentication enabled.
 [+] : New Protocol Components: "Broker" allows to use more than one protocol using a single connection.

 [*] : Fixed Bug loading resources when is a library
 [*] : Fixed Bug OnException Event
 [*] : Fixed Bug when a client has more than one protocol assigned
 [*] : Fixed Bug handling multithreading messages
 [*] : Fixed Bug Firefox Close Code

 [-] : Removed all WITH statements

 [/] : Removed sgcWebSocket_CS.pas, now it's defined on sgcWebSockets_Classes.pas


## 2.3: 2013 March

 [+] : Added Support to Lazarus / FreePascal.
 [+] : Added Support to Delphi 7 (upgrading to Indy 10)
 [+] : Improved performance and reliability on websocket connections.
 [+] : New Property "DocumentRoot": if defined, automatically publish http response files.
 [+] : New Event "DataSession": allows to assign a user session object (database connection, user session data...)
 [+] : New Property "Authentication": allows to authenticate WebSocket Connections using a user/password.
 [+] : New Property "ThreadPool" on server components
 [+] : New Property "AsyncEvents": allows to define which method used to notify websocket events: none, asynchronous (is the default) and synchronous.
 [+] : New Property "HeartBeat": sends a ping every x seconds (disabled by default). 
 [+] : New Property "ValidateUTF8": validates utf8 messages (disabled by default).
 [+] : New Property "JavascriptFiles" on server components: allows requests to server built-in javascript libraries.
 [+] : New Property "HTMLFiles" on server components: allows requests to server built-in html files.

 [*] : Fixed Bug OnHandShake event not fired
 [*] : Fixed exception when socket closes connection
 [*] : Fixed Bug when receiving fragmented message with control code
 [*] : Fixed Bug when optcode is not recognized 
 [*] : Fixed Bug with RSV bits when no extension is negotiated
 [*] : Fixed Bug when payload is empty
 [*] : Fixed exception reading Guid
 [*] : Fixed Bug with binary Ping Frames
 [*] : Fixed Bug with Ping payload greater than 125 octets

 [/] : Javascript libraries: binary messages are now received using "stream" event (before, this messages were received on "message" event).
 [/] : Protocols are now based on JSON-RPC 2.0 (except WAMP protocol which uses his own protocol).


## 2.2: 2013 January

 [+] : New WebSocket Protocol: WAMP
         Open Source SubProtocol
         Provides two asynchronous  messaging patterns:
           - RPC
           - Subscription / Publish
 [+] : New WebSocket Protocol: WebRTC
         Open Project that enables web browsers with Real-Time Communications (RTC)
         Currently Only Chrome it's supported
         WebRTC is still on Beta Status
 [+] : Added support for read/write JSON lists
 [+] : Server Components: Added Arguments Exclude and Include List of guids
 [+] : Javascript source is minified to save bandwith.
 [+] : Added methods to send stream on sub-protocol base component.

 [*] : Fixed Bug on Test Pages using ssl connection
 [*] : Fixed Bug on Read UnMasked Frame
 [*] : Fixed Bug on Client Component when Error #10054 raised.




## 2.1: 2012 November

 [+] : New WebSocket Extension: Deflate-frame, allows to compress exchanged data.
 [+] : Server Components: New Event "OnBinary" fired when a clients sends a binary message.
 [+] : Server Components: Overloaded BroadCast and WriteData to allow to send streams.
 [+] : Server Components: New Property "SSL", allows to stablish SSL connections with clients.
 [+] : TsgcWebSocketClient: New Event "OnBinary" fired when client receives a binary message. 
 [+] : TsgcWebSocketClient: Overloaded WriteData to allow to send streams.
 [+] : TsgcWebSocketClient: New Event "OnException" fired when a Exception is raised outside WebSocket Connection.
 [+] : Server Components: New Property "Bindings".
 [+] : Server Components: New Property "OriginsAllowed", on new connection, checks if origin is allowed (by default accepts all origins).
 [+] : TsgcWebSocketClient: New Property "Options", allows to define which Parameters / Origin are sent on opening HandShake.
 [+] : TsgcWSConnection: New Property "Port" (connection peer port).
 [+] : TsgcWSConnection: New Property "RecBytes" (connection bytes received).
 [+] : TsgcWSConnection: New Property "SendBytes", (connection bytes sent).

 [*] : Fixed Bug re-connectiong from a SSL Client connection.
 [*] : Fixed some memory leaks.
 [*] : Fixed bug on Protocol Hixie76.
 [*] : FIxed bug UTF-8 messages.

 [/] : TsgcWebSocketClient: Property "Parameters" now is a Property of "Options"




## 2.0: 2012 October

 [+] : RAD Studio XE3 Supported.
 [+] : Added Support to Firemonkey (Win32, Win64 and MacOSX).
 [+] : Added support to create custom sub-protocols.
 [+] : TsgcWebSocketHTTPServer: New Component! WebSocket Server that includes HTTP Server to share WebSocket and HTTP connections over the same port.
 [+] : TsgcWebSocketClient_SocketIO: New Component! WebSocket Client that allows to connect to Socket.IO Servers.
 [+] : TsgcWSPServer_sgc: New Component! server that uses JSON to broadcast messages to all clients.
 [+] : TsgcWSPClient_sgc: New Component! client that uses JSON messages to communicate with server.
 [+] : TsgcWSPServer_dataset: New Component! broadcast dataset changes to all clients connected.
 [+] : TsgcWSPClient_dataset: New Component! automatically updates client dataset from server changes.
 [+] : TsgcWebSocketServer: Added javascript browser client support. 
 [+] : TsgcWebSocketServer: Added built-in html pages to test browser websocket connection.
 [+] : TsgcWebSocketServer: New Property "MaxConnections". 
 [+] : TsgcWebSocketClient: New Property "Proxy", now supports WebSocket Protocol over HTTP Proxy Connections.
 [+] : TsgcWebSocketClient: New Method "Ping".
 [+] : TsgcWebSocketClient: New Property "MaxConnections".
 [+] : TsgcWebSocketClient: New Property "Parameters", allows to pass parameters on Handshake.

 [*] : Fixed RangeCheck Error 
 [*] : Fixed Unicode Warnings
 [*] : Fixed Active Property Error
 [*] : TsgcWebSocketClient: OnConnect Event only fired if HandShake is correct

 [/] : TsgcWebScocketServer: Deleted property Protocols
 [/] : TsgcWebSocketClient: Deleted property Protocol
 [/] : Subscription / UnSubscription methods now are implemented on protocol components.



## 1.2: 2012 June

 [+] : TsgcWebSocketServer: Now Supports draft Hixie76, Safari and iOS browsers now are supported from version 4.2
 [+] : TsgcIWWebSocketClient: New Property "Mode": [Native, Emulation] Allows to emulate socket connections
         on webbrowsers that don't support websockets natively (like internet explorer).
 [+] : TsgcWebSocketServer: New Property "Specifications": [RFC6455, Hixie76] defines which specifications are supported.
 [+] : TsgcWebSocketClient: New Property "Specifications": [RFC6455, Hixie76] defines which specifications are supported.
 [+] : TsgcWebSocketServer: Method "Broadcast" now accepts "Subscription" allowing to send custom messages only to subscribed clients
 [+] : TsgcWebSocketServer: New Event "OnSubscription" fired when a client Subscribes to a channel 
 [+] : TsgcWebSocketServer: New Event "OnUnSubscription" fired when a client UnSubscribes to a channel
 [+] : TsgcWebSocketClient: New Methods: "Subscribe" and "Unsubscribe" allowing to subscribe to custom channels
 [+] : TsgcIWWebSocketClient: New Methods: "Subscribe" and "Unsubscribe" allowing to subscribe to custom channels

 [*] : TsgcWebSocketServer: Fixed bug reading get parameters
 [*] : TsgcWebSocketServer: Fixed bug OnMessage Event

## 1.1: 2012 May

 [+] : TsgcWebSocketServer: allows to Send a Message to a single Client
 [+] : TsgcWebSocketServer: New Property "Connections" to get access to all client connections
 [+] : TsgcWebSocketServer: New Event "OnHandshake" allows to modify handshake before send to client
 [+] : TsgcWebSocketClient: New Event "OnHandshake" allows to modify handshake before send to server
 [+] : TsgcWebSocketClient: New Property "TLS" allows to stablish secure connections
 [+] : TsgcIWWebSocketClient: New Property "TLS" allows to stablish secure connections
 [+] : TsgcWebSocketServer: Event "OnDisconnect" now has "Code" to get close reason if applicable

 [*] : TsgcWebSocketclient: Fixed error assigning properties at runtime
 [*] : TsgcWebSocketServer: Fixed broadcast error on Chrome (v.19) 
 [*] : TsgcIWWebSocketClient: Fixed close connection error on Chrome (v.19) 
 [*] : TsgcWebSocketClient: error reading handshake status
 [*] : TsgcWebSocketClient: in some environments, OnDisconnect event was not fired
 [*] : TsgcIWWebSocketClient: Fixed close connection error

 [/] : TsgcWebSocketServer: Event "OnDisconnect" introduced parameter "Code"
 [/] : TsgcWebSocketClient: Event "OnDisconnect" introduced parameter "Code"

## 1.0: 2012 April

 [+] : First Version








