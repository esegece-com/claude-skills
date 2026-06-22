# Bundled Resources (HTML / JavaScript)

sgcWebSockets ships a set of browser-side assets (JavaScript, HTML, CSS) under `delphi\resources\`. These are compiled into the library as binary resources (`sgcResources.rc` / `sgcResources.RES`, and `sgcHTMLResources` for the sgcHTML components) and are served or embedded by the **server** components at runtime, so a browser client works without any external CDN.

You normally do not reference these files directly; the server components emit them. This page lists what is bundled so you know what the server side can deliver.

## WebSocket JavaScript client

- `sgcWebSockets.html` - browser WebSocket client
- `sgcWebSockets.js` - browser WebSocket client
- `sgcWebSockets.min.js` - browser WebSocket client
- `sgcWebSockets.module.js` - browser WebSocket client
- `sgcWebSockets.module.min.js` - browser WebSocket client
- `sgcWebSocketsEventSource.js` - Server-Sent Events client
- `sgcWebSocketsEventSource.min.js` - Server-Sent Events client
- `sgcWebSocketsFlash.js` - legacy Flash fallback
- `sgcWebSocketsFlash.min.js` - legacy Flash fallback
- `WebSocketMain.swf` - legacy Flash fallback

## sgcHTML / htmx UI

- `bootstrap.bundle.min.js` - Bootstrap UI assets
- `bootstrap.min.css` - Bootstrap UI assets
- `chart.umd.min.js` - Chart.js charting
- `htmx.min.js` - htmx runtime
- `htmx-ext-ws.min.js` - htmx runtime
- `sgcHTMLResources.bat` - compiled sgcHTML resources
- `sgcHTMLResources.rc` - compiled sgcHTML resources
- `sgcHTMLResources.RES` - compiled sgcHTML resources
- `sgcHTMX.min.js` - htmx runtime

## WebRTC

- `apprtc.esegece.com.css`
- `apprtc.esegece.com.js`
- `apprtc.esegece.com.min.js`
- `sgcRTCMultiConnection.css`
- `sgcRTCMultiConnection.html`
- `sgcRTCMultiConnection.js`
- `sgcRTCMultiConnection.min.css`
- `sgcRTCMultiConnection.min.js`
- `sgcRTCMultiConnection_AudioConferencing.html`
- `sgcRTCMultiConnection_ScreenSharing.html`
- `sgcRTCMultiConnection_VideoBroadcasting.html`
- `sgcRTCMultiConnection_VideoConferencing.html`
- `webrtc.esegece.com.html`
- `webrtc.esegece.com.js`
- `webrtc.esegece.com.min.js`

## Web Push

- `sgcWebPush.html` - Web Push client
- `sgcWebPush.js` - Web Push client
- `sgcWebPush.min.js` - Web Push client
- `sgcWebPushServiceWorker.js` - Web Push service worker
- `sgcWebPushServiceWorker.min.js` - Web Push service worker

## WebAuthn

- `sgcWebAuthn.html` - WebAuthn client
- `sgcWebAuthn.min.js` - WebAuthn client
- `sgcWebAuthn_ws.html` - WebAuthn client

## Protocol JavaScript clients

- `dataset.esegece.com.html`
- `dataset.esegece.com.js`
- `dataset.esegece.com.min.js`
- `esegece.com.html`
- `esegece.com.js`
- `esegece.com.min.js`
- `files.esegece.com.html`
- `files.esegece.com.js`
- `files.esegece.com.min.js`
- `presence.esegece.com.html`
- `presence.esegece.com.js`
- `presence.esegece.com.min.js`
- `wamp.esegece.com.html`
- `wamp.esegece.com.js`
- `wamp.esegece.com.min.js`

## OAuth2

- `sgcOAuth2_Authorization.html` - OAuth2 authorization page

## Build / packaging

- `sgcResources.bat` - resource build script
- `sgcResources.rc` - resource compiler script
- `sgcResources.RES` - compiled binary resources

