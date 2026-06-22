# TIdHTTPResponse

kind: class
unit: IdHTTP

## Properties

| Delphi | Type |
| --- | --- |
| `KeepAlive: Boolean` | `Boolean` |
| `MetaHTTPEquiv: TIdMetaHTTPEquiv (read-only)` | [TIdMetaHTTPEquiv](./TIdMetaHTTPEquiv.md) |
| `ResponseText: string` | `string` |
| `ResponseCode: Integer` | `Integer` |
| `ResponseVersion: TIdHTTPProtocolVersion` | [TIdHTTPProtocolVersion](./TIdHTTPProtocolVersion.md) |
| `ContentStream: TStream` | `TStream` |
| `AcceptPatch: string` | `string` |
| `AcceptRanges: string` | `string` |
| `Location: string` | `string` |
| `ProxyConnection: string` | `string` |
| `ProxyAuthenticate: TIdHeaderList` | [TIdHeaderList](./TIdHeaderList.md) |
| `Server: string` | `string` |
| `WWWAuthenticate: TIdHeaderList` | [TIdHeaderList](./TIdHeaderList.md) |
| `OwnerComponent: TComponent (read-only)` | `TComponent` |
| `HasContentLength: Boolean (read-only)` | `Boolean` |
| `HasContentRange: Boolean (read-only)` | `Boolean` |
| `HasContentRangeInstance: Boolean (read-only)` | `Boolean` |
| `RawHeaders: TIdHeaderList (read-only)` | [TIdHeaderList](./TIdHeaderList.md) |
| `CacheControl: String` | `String` |
| `CharSet: String` | `String` |
| `Connection: string` | `string` |
| `ContentDisposition: string` | `string` |
| `ContentEncoding: string` | `string` |
| `ContentLanguage: string` | `string` |
| `ContentLength: Int64` | `Int64` |
| `ContentRangeEnd: Int64` | `Int64` |
| `ContentRangeStart: Int64` | `Int64` |
| `ContentRangeInstanceLength: Int64` | `Int64` |
| `ContentRangeUnits: String` | `String` |
| `ContentType: string` | `string` |
| `ContentVersion: string` | `string` |
| `CustomHeaders: TIdHeaderList` | [TIdHeaderList](./TIdHeaderList.md) |
| `Date: TDateTime` | `TDateTime` |
| `ETag: string` | `string` |
| `Expires: TDateTime` | `TDateTime` |
| `LastModified: TDateTime` | `TDateTime` |
| `Pragma: string` | `string` |
| `TransferEncoding: string` | `string` |

## Methods

```pascal
procedure Clear;
procedure AfterConstruction;
```

