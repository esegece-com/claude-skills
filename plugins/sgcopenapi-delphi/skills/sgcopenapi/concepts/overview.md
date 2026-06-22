# Overview

sgcOpenAPI is an eSeGeCe component library for Delphi and C++Builder. This skill ships its public API surface only (properties, events, methods), so you can write correct code without the library source.

## Uses-clause rule

Each component lives in a specific unit. Find the component in `reference/components-index.md`, then add the `unit:` value shown on its `reference/api/<Component>.md` page to your `uses` clause. Without that unit the component type is not visible to the compiler.

Only public and published members are documented in this skill. Always verify a member exists on the component's `reference/api/` page before using it.

## See also

- `reference/components-index.md` lists every component and its `unit`.
- `examples/index.md` is the full demo catalog; `examples/<Component>.md` is a real usage snippet.
- `reference/history.md` lists what changed in each sgcOpenAPI release.

