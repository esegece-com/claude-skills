# TsgcOpenAPI_Object

unit: sgcOpenAPI_Classes

Add `sgcOpenAPI_Classes` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Initialized: Boolean` | `Boolean` | `__property bool Initialized;` |
| `_Ref: string` | `string` | `__property UnicodeString _Ref;` |

## Methods

Delphi

```pascal
function Clone: TsgcOpenAPI_Object;
procedure Read(const aObject: TJSONObject);
```

C++Builder

```cpp
TsgcOpenAPI_Object * __fastcall Clone();
void __fastcall Read(const TJSONObject * aObject);
```

