# TIdMetaHTTPEquiv

kind: class
unit: IdHTTPHeaderInfo

## Properties

| Delphi | Type |
| --- | --- |
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
procedure ProcessMetaHTTPEquiv(AStream: TStream);
procedure AfterConstruction;
procedure Clear;
```

