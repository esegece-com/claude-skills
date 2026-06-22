# TsgcOpenAPI_Parser_Client_Pascal

unit: sgcOpenAPI_Parser_Client_Pascal

Add `sgcOpenAPI_Parser_Client_Pascal` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OpenAPI_JSON: Boolean` | `Boolean` | `__property bool OpenAPI_JSON;` |
| `Text: string (read-only)` | `string` | `__property UnicodeString Text /* read-only */;` |
| `Methods: TsgcOpenAPI_Methods` | [TsgcOpenAPI_Methods](../types/TsgcOpenAPI_Methods.md) | `__property TsgcOpenAPI_Methods * Methods;` |
| `Classes: TsgcOpenAPI_Classes` | [TsgcOpenAPI_Classes](../types/TsgcOpenAPI_Classes.md) | `__property TsgcOpenAPI_Classes * Classes;` |
| `Arrays: TsgcOpenAPI_Arrays` | [TsgcOpenAPI_Arrays](../types/TsgcOpenAPI_Arrays.md) | `__property TsgcOpenAPI_Arrays * Arrays;` |
| `Enums: TsgcOpenAPI_Enums` | [TsgcOpenAPI_Enums](../types/TsgcOpenAPI_Enums.md) | `__property TsgcOpenAPI_Enums * Enums;` |
| `Primitives: TsgcOpenAPI_Primitives` | [TsgcOpenAPI_Primitives](../types/TsgcOpenAPI_Primitives.md) | `__property TsgcOpenAPI_Primitives * Primitives;` |
| `Amazon: Boolean` | `Boolean` | `__property bool Amazon;` |
| `Google: Boolean` | `Boolean` | `__property bool Google;` |
| `Microsoft: Boolean` | `Boolean` | `__property bool Microsoft;` |
| `BaseURL: string` | `string` | `__property UnicodeString BaseURL;` |
| `Comments: string` | `string` | `__property UnicodeString Comments;` |
| `Documentation: Boolean` | `Boolean` | `__property bool Documentation;` |
| `OpenAPIAuthBasic: Boolean` | `Boolean` | `__property bool OpenAPIAuthBasic;` |
| `OpenAPIAuthJWT: Boolean` | `Boolean` | `__property bool OpenAPIAuthJWT;` |
| `OpenAPIAuthOAuth2: Boolean` | `Boolean` | `__property bool OpenAPIAuthOAuth2;` |
| `OpenAPIAuthToken: Boolean` | `Boolean` | `__property bool OpenAPIAuthToken;` |
| `OpenAPIClasses: Boolean` | `Boolean` | `__property bool OpenAPIClasses;` |
| `OpenAPINamespace: string` | `string` | `__property UnicodeString OpenAPINamespace;` |
| `OpenAPIClassName: string` | `string` | `__property UnicodeString OpenAPIClassName;` |
| `MethodsName: TsgcOAPI_MethodsName` | [TsgcOAPI_MethodsName](../types/TsgcOAPI_MethodsName.md) | `__property TsgcOAPI_MethodsName * MethodsName;` |
| `OpenAPITrial: Boolean` | `Boolean` | `__property bool OpenAPITrial;` |
| `OpenAPI: string` | `string` | `__property UnicodeString OpenAPI;` |
| `Info: TsgcOpenAPI_Object_Info` | [TsgcOpenAPI_Object_Info](../types/TsgcOpenAPI_Object_Info.md) | `__property TsgcOpenAPI_Object_Info * Info;` |
| `Servers: TsgcOpenAPI_Object_Servers` | [TsgcOpenAPI_Object_Servers](../types/TsgcOpenAPI_Object_Servers.md) | `__property TsgcOpenAPI_Object_Servers * Servers;` |
| `Paths: TsgcOpenAPI_Object_Paths` | [TsgcOpenAPI_Object_Paths](../types/TsgcOpenAPI_Object_Paths.md) | `__property TsgcOpenAPI_Object_Paths * Paths;` |
| `Components: TsgcOpenAPI_Object_Components` | [TsgcOpenAPI_Object_Components](../types/TsgcOpenAPI_Object_Components.md) | `__property TsgcOpenAPI_Object_Components * Components;` |
| `Security: TsgcOpenAPI_Object_Security` | [TsgcOpenAPI_Object_Security](../types/TsgcOpenAPI_Object_Security.md) | `__property TsgcOpenAPI_Object_Security * Security;` |
| `Tags: TsgcOpenAPI_Object_Tags` | [TsgcOpenAPI_Object_Tags](../types/TsgcOpenAPI_Object_Tags.md) | `__property TsgcOpenAPI_Object_Tags * Tags;` |
| `ExternalDocs: TsgcOpenAPI_Object_ExternalDocs` | [TsgcOpenAPI_Object_ExternalDocs](../types/TsgcOpenAPI_Object_ExternalDocs.md) | `__property TsgcOpenAPI_Object_ExternalDocs * ExternalDocs;` |

## Methods

Delphi

```pascal
function GetDefaultServer: string;
procedure SaveToFile(const aFileName: string);
function GetVersion(aValue: string): string;
function GetVersionFromFile(const aFileName: string): string;
procedure Read(const aValue: string);
procedure ReadFromFile(const aFileName: string);
```

C++Builder

```cpp
UnicodeString __fastcall GetDefaultServer();
void __fastcall SaveToFile(const UnicodeString aFileName);
UnicodeString __fastcall GetVersion(UnicodeString aValue);
UnicodeString __fastcall GetVersionFromFile(const UnicodeString aFileName);
void __fastcall Read(const UnicodeString aValue);
void __fastcall ReadFromFile(const UnicodeString aFileName);
```

