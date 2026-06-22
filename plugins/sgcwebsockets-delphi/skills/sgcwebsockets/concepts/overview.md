# Overview

sgcWebSockets is the eSeGeCe networking and communication component suite for Delphi and C++Builder, providing WebSocket, HTTP/2/3, AI/LLM, MQTT, AMQP, MCP, SSE, WAMP, P2P/WebRTC, IoT and 30+ API integrations as drop-in components.

## Uses-clause rule

Each component lives in a specific unit. Find the component in `reference/components-index.md`, then add the `unit:` value shown on its `reference/api/<Component>.md` page to your `uses` clause. Without that unit the component type is not visible to the compiler.

## Getting started: a WebSocket client

Instantiate `TsgcWebSocketClient` (unit `sgcWebSocket`), set `Host` and `Port`, enable `TLS` for secure connections, handle the `OnConnect`, `OnMessage` and `OnError` events, then call `Connect`.

```pascal
uses sgcWebSocket;

var oClient: TsgcWebSocketClient;
begin
  oClient := TsgcWebSocketClient.Create(nil);
  oClient.Host := 'echo.websocket.org';
  oClient.Port := 443;
  oClient.TLS := True;
  oClient.OnConnect := DoConnect;
  oClient.OnMessage := DoMessage;
  oClient.OnError := DoError;
  oClient.Connect;
end;
```

See `examples/TsgcWebSocketClient.md` for a real extracted snippet and `reference/api/TsgcWebSocketClient.md` for the full member list.

## Getting started: a WebSocket server

Instantiate `TsgcWebSocketServer` (unit `sgcWebSocket`), set `Port`, handle `OnMessage`, then set `Active := True` to start listening.

```pascal
oServer := TsgcWebSocketServer.Create(nil);
oServer.Port := 8080;
oServer.OnMessage := DoServerMessage;
oServer.Active := True;
```

Only public and published members are documented in this skill. Always verify a member exists on the component's `reference/api/` page before using it.

## See also

- `concepts/editions-and-features.md` groups components by edition and explains the Indy-by-edition rule (Standard/Professional use Delphi's Indy; Enterprise/All-Access use eSeGeCe's custom Indy).
- `concepts/resources.md` lists the bundled browser-side client assets (JavaScript, HTML, CSS) the server components serve or embed.

