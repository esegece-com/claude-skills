# TsgcAuthenticodeVerifier

unit: sgcSign_Authenticode

Add `sgcSign_Authenticode` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function Verify(const aFilePath: string): TsgcAuthenticodeVerifyResult;
```

C++Builder

```cpp
TsgcAuthenticodeVerifyResult * __fastcall Verify(const UnicodeString aFilePath);
```

