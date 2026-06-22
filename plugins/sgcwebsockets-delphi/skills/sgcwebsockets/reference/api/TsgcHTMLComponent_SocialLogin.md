# TsgcHTMLComponent_SocialLogin

unit: sgcHTML_Component_SocialLogin
Edition: All-Access

Add `sgcHTML_Component_SocialLogin` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Providers: TsgcHTMLSocialProviderItems` | [TsgcHTMLSocialProviderItems](../types/TsgcHTMLSocialProviderItems.md) | `__property TsgcHTMLSocialProviderItems * Providers;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Subtitle: string` | `string` | `__property UnicodeString Subtitle;` |
| `Layout: TsgcHTMLSocialLoginLayout` | [TsgcHTMLSocialLoginLayout](../types/TsgcHTMLSocialLoginLayout.md) | `__property TsgcHTMLSocialLoginLayout * Layout;` |
| `ShowDivider: Boolean` | `Boolean` | `__property bool ShowDivider;` |
| `DividerText: string` | `string` | `__property UnicodeString DividerText;` |
| `LoginID: string` | `string` | `__property UnicodeString LoginID;` |
| `MaxWidth: string` | `string` | `__property UnicodeString MaxWidth;` |
| `ShowIcons: Boolean` | `Boolean` | `__property bool ShowIcons;` |
| `ButtonPadding: string` | `string` | `__property UnicodeString ButtonPadding;` |
| `ButtonBorderRadius: string` | `string` | `__property UnicodeString ButtonBorderRadius;` |
| `HTML: string (read-only)` | `string` | `__property UnicodeString HTML /* read-only */;` |
| `PageBuilder: TsgcHTMLPageBuilder` | [TsgcHTMLPageBuilder](../types/TsgcHTMLPageBuilder.md) | `__property TsgcHTMLPageBuilder * PageBuilder;` |
| `Section: string` | `string` | `__property UnicodeString Section;` |
| `SectionTitle: string` | `string` | `__property UnicodeString SectionTitle;` |
| `SectionOrder: Integer` | `Integer` | `__property int SectionOrder;` |
| `ColumnWidth: TsgcHTMLColWidth` | [TsgcHTMLColWidth](../types/TsgcHTMLColWidth.md) | `__property TsgcHTMLColWidth * ColumnWidth;` |
| `RowGroup: Integer` | `Integer` | `__property int RowGroup;` |
| `ComponentVisible: Boolean` | `Boolean` | `__property bool ComponentVisible;` |
| `DataSource: TDataSource` | `TDataSource` | `__property TDataSource * DataSource;` |
| `DataAutoRefresh: Boolean` | `Boolean` | `__property bool DataAutoRefresh;` |
| `HTMXEngine: TComponent` | `TComponent` | `__property TComponent * HTMXEngine;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure AddProvider(aProvider: TsgcHTMLSocialProvider; const aClientID, aRedirectURI: string; const aScope: string = '');
```

C++Builder

```cpp
void __fastcall AddProvider(TsgcHTMLSocialProvider * aProvider, const UnicodeString aClientID, const UnicodeString aRedirectURI, const UnicodeString aScope = '');
```

