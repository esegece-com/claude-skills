# TsgcHTMLComponent_WebAuthnLogin

unit: sgcHTML_Component_WebAuthnLogin

Add `sgcHTML_Component_WebAuthnLogin` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Mode: TsgcHTMLWebAuthnMode` | [TsgcHTMLWebAuthnMode](../types/TsgcHTMLWebAuthnMode.md) | `__property TsgcHTMLWebAuthnMode * Mode;` |
| `RegisterURL: string` | `string` | `__property UnicodeString RegisterURL;` |
| `AuthenticateURL: string` | `string` | `__property UnicodeString AuthenticateURL;` |
| `CallbackURL: string` | `string` | `__property UnicodeString CallbackURL;` |
| `RegisterButtonText: string` | `string` | `__property UnicodeString RegisterButtonText;` |
| `AuthenticateButtonText: string` | `string` | `__property UnicodeString AuthenticateButtonText;` |
| `RegisterButtonStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * RegisterButtonStyle;` |
| `AuthenticateButtonStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * AuthenticateButtonStyle;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Description: string` | `string` | `__property UnicodeString Description;` |
| `WebAuthnID: string` | `string` | `__property UnicodeString WebAuthnID;` |
| `ShowPasskeyIcon: Boolean` | `Boolean` | `__property bool ShowPasskeyIcon;` |
| `SuccessAlertClass: string` | `string` | `__property UnicodeString SuccessAlertClass;` |
| `ErrorAlertClass: string` | `string` | `__property UnicodeString ErrorAlertClass;` |
| `SuccessAlertStyle: TsgcHTMLAlertStyle` | [TsgcHTMLAlertStyle](../types/TsgcHTMLAlertStyle.md) | `__property TsgcHTMLAlertStyle * SuccessAlertStyle;` |
| `ErrorAlertStyle: TsgcHTMLAlertStyle` | [TsgcHTMLAlertStyle](../types/TsgcHTMLAlertStyle.md) | `__property TsgcHTMLAlertStyle * ErrorAlertStyle;` |
| `CustomScript: string` | `string` | `__property UnicodeString CustomScript;` |
| `PasskeyIconSize: string` | `string` | `__property UnicodeString PasskeyIconSize;` |
| `UsernameSelector: string` | `string` | `__property UnicodeString UsernameSelector;` |
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

