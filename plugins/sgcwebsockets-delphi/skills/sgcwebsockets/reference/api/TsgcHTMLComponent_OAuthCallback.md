# TsgcHTMLComponent_OAuthCallback

unit: sgcHTML_Component_OAuthCallback
Edition: All-Access

Add `sgcHTML_Component_OAuthCallback` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Status: TsgcHTMLOAuthCallbackStatus` | [TsgcHTMLOAuthCallbackStatus](../types/TsgcHTMLOAuthCallbackStatus.md) | `__property TsgcHTMLOAuthCallbackStatus * Status;` |
| `ProviderName: string` | `string` | `__property UnicodeString ProviderName;` |
| `UserName: string` | `string` | `__property UnicodeString UserName;` |
| `UserEmail: string` | `string` | `__property UnicodeString UserEmail;` |
| `UserAvatar: string` | `string` | `__property UnicodeString UserAvatar;` |
| `ErrorMessage: string` | `string` | `__property UnicodeString ErrorMessage;` |
| `RedirectURL: string` | `string` | `__property UnicodeString RedirectURL;` |
| `RedirectDelay: Integer` | `Integer` | `__property int RedirectDelay;` |
| `CallbackID: string` | `string` | `__property UnicodeString CallbackID;` |
| `ShowUserInfo: Boolean` | `Boolean` | `__property bool ShowUserInfo;` |
| `SuccessIconHTML: string` | `string` | `__property UnicodeString SuccessIconHTML;` |
| `ErrorIconHTML: string` | `string` | `__property UnicodeString ErrorIconHTML;` |
| `SuccessIconColor: string` | `string` | `__property UnicodeString SuccessIconColor;` |
| `ErrorIconColor: string` | `string` | `__property UnicodeString ErrorIconColor;` |
| `SuccessIconColorEnum: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * SuccessIconColorEnum;` |
| `ErrorIconColorEnum: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * ErrorIconColorEnum;` |
| `SuccessIconText: string` | `string` | `__property UnicodeString SuccessIconText;` |
| `ErrorIconText: string` | `string` | `__property UnicodeString ErrorIconText;` |
| `RedirectMethod: TsgcHTMLOAuthRedirectMethod` | [TsgcHTMLOAuthRedirectMethod](../types/TsgcHTMLOAuthRedirectMethod.md) | `__property TsgcHTMLOAuthRedirectMethod * RedirectMethod;` |
| `MaxWidth: string` | `string` | `__property UnicodeString MaxWidth;` |
| `AvatarSize: Integer` | `Integer` | `__property int AvatarSize;` |
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

