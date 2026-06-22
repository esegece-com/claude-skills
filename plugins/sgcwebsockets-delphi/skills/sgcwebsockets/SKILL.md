---
name: sgcwebsockets
description: Use when writing Delphi or C++Builder code that uses the eSeGeCe sgcWebSockets library (WebSocket, HTTP/2/3, AI/LLM, MQTT, AMQP, MCP, WebRTC, IoT and 30+ API integrations). Provides the public component API reference (properties, methods, events), the unit/uses mapping, edition availability, and usage examples for users who do not have the library source code.
---

# sgcWebSockets

sgcWebSockets is the eSeGeCe networking and communication component suite for Delphi and C++Builder. This skill ships the public API surface only (properties, events, methods), so you can write correct code without the library source.

## Routing

- **Find a component**: `reference/components-index.md` lists every component, its `unit`, and its edition, grouped by Reg module.
- **Uses clause**: add the component's `unit:` value (shown on its API page) to your `uses` clause. Nothing compiles without it.
- **API detail**: `reference/api/<Component>.md` has the Properties, Events and Methods, each in both Delphi and C++Builder form.
- **Option / enum / event types**: property and event types link to `reference/types/<TypeName>.md`, which documents the sub-properties of option classes, the values of enums, and the parameter list of event handlers.
- **Examples**: `examples/index.md` is the full demo catalog; `examples/<Component>.md` is a focused, real usage snippet for the most-used components.
- **Concepts**: `concepts/overview.md` (getting started + uses-clause rule) and `concepts/editions-and-features.md` (which components your edition includes).
- **Bundled resources**: `concepts/resources.md` lists the browser-side assets (JavaScript, HTML, CSS) the server components serve or embed, so a browser client works without an external CDN.
- **Version history**: `reference/history.md` lists what changed in each sgcWebSockets release.

## Editions

Components are gated by edition (Professional, Enterprise, All-Access) or by a feature define. Check the edition column in the components index, or `concepts/editions-and-features.md`, before relying on a component.

Only public and published members are documented. Method bodies, private fields and protected members are intentionally not included.

