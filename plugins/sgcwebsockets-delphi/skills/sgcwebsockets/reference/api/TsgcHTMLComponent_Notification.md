# TsgcHTMLComponent_Notification

unit: sgcHTML_Component_Notification
Edition: All-Access

Add `sgcHTML_Component_Notification` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `UnreadCount: Integer (read-only)` | `Integer` | `__property int UnreadCount /* read-only */;` |
| `Items: TsgcHTMLNotificationItems` | [TsgcHTMLNotificationItems](../types/TsgcHTMLNotificationItems.md) | `__property TsgcHTMLNotificationItems * Items;` |
| `NotificationID: string` | `string` | `__property UnicodeString NotificationID;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `EmptyText: string` | `string` | `__property UnicodeString EmptyText;` |
| `MaxVisible: Integer` | `Integer` | `__property int MaxVisible;` |
| `BellIcon: string` | `string` | `__property UnicodeString BellIcon;` |
| `ShowBadge: Boolean` | `Boolean` | `__property bool ShowBadge;` |
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
procedure AddNotification(const aTitle, aMessage: string; aColor: TsgcHTMLColor = hcPrimary; const aTimestamp: string = '');
function GetBadgeHTML: string;
```

C++Builder

```cpp
void __fastcall AddNotification(const UnicodeString aTitle, const UnicodeString aMessage, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aTimestamp = '');
UnicodeString __fastcall GetBadgeHTML();
```

