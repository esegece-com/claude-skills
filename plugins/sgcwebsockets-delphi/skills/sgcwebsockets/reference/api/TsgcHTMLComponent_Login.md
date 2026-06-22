# TsgcHTMLComponent_Login

unit: sgcHTML_Component_Login
Edition: All-Access

Add `sgcHTML_Component_Login` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `FormAction: string` | `string` | `__property UnicodeString FormAction;` |
| `FormMethod: string` | `string` | `__property UnicodeString FormMethod;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Subtitle: string` | `string` | `__property UnicodeString Subtitle;` |
| `UserLabel: string` | `string` | `__property UnicodeString UserLabel;` |
| `UserPlaceholder: string` | `string` | `__property UnicodeString UserPlaceholder;` |
| `PasswordLabel: string` | `string` | `__property UnicodeString PasswordLabel;` |
| `PasswordPlaceholder: string` | `string` | `__property UnicodeString PasswordPlaceholder;` |
| `ButtonText: string` | `string` | `__property UnicodeString ButtonText;` |
| `ButtonClass: string` | `string` | `__property UnicodeString ButtonClass;` |
| `ErrorMessage: string` | `string` | `__property UnicodeString ErrorMessage;` |
| `SuccessMessage: string` | `string` | `__property UnicodeString SuccessMessage;` |
| `ShowRememberMe: Boolean` | `Boolean` | `__property bool ShowRememberMe;` |
| `LoginStyle: TsgcHTMLLoginStyle` | [TsgcHTMLLoginStyle](../types/TsgcHTMLLoginStyle.md) | `__property TsgcHTMLLoginStyle * LoginStyle;` |
| `FormID: string` | `string` | `__property UnicodeString FormID;` |
| `CSSClass: string` | `string` | `__property UnicodeString CSSClass;` |
| `LogoHTML: string` | `string` | `__property UnicodeString LogoHTML;` |
| `FooterHTML: string` | `string` | `__property UnicodeString FooterHTML;` |
| `MaxWidth: string` | `string` | `__property UnicodeString MaxWidth;` |
| `ButtonStyleEnum: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * ButtonStyleEnum;` |
| `MinHeight: string` | `string` | `__property UnicodeString MinHeight;` |
| `BackgroundClass: string` | `string` | `__property UnicodeString BackgroundClass;` |
| `LogoText: string` | `string` | `__property UnicodeString LogoText;` |
| `FooterLinkText: string` | `string` | `__property UnicodeString FooterLinkText;` |
| `FooterLinkURL: string` | `string` | `__property UnicodeString FooterLinkURL;` |
| `BootstrapCSSPath: string` | `string` | `__property UnicodeString BootstrapCSSPath;` |
| `BootstrapJSPath: string` | `string` | `__property UnicodeString BootstrapJSPath;` |
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
function GetFullPageHTML(const aPageTitle: string = ''): string;
procedure SetLogoText(const aText: string);
procedure SetFooterText(const aText: string);
```

C++Builder

```cpp
UnicodeString __fastcall GetFullPageHTML(const UnicodeString aPageTitle = '');
void __fastcall SetLogoText(const UnicodeString aText);
void __fastcall SetFooterText(const UnicodeString aText);
```

