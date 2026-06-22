# TsgcHTMLComponent_Carousel

unit: sgcHTML_Component_Carousel
Edition: All-Access

Add `sgcHTML_Component_Carousel` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Items: TsgcHTMLCarouselItems` | [TsgcHTMLCarouselItems](../types/TsgcHTMLCarouselItems.md) | `__property TsgcHTMLCarouselItems * Items;` |
| `CarouselID: string` | `string` | `__property UnicodeString CarouselID;` |
| `ShowIndicators: Boolean` | `Boolean` | `__property bool ShowIndicators;` |
| `ShowControls: Boolean` | `Boolean` | `__property bool ShowControls;` |
| `Autoplay: Boolean` | `Boolean` | `__property bool Autoplay;` |
| `Interval: Integer` | `Integer` | `__property int Interval;` |
| `Transition: TsgcHTMLCarouselTransition` | [TsgcHTMLCarouselTransition](../types/TsgcHTMLCarouselTransition.md) | `__property TsgcHTMLCarouselTransition * Transition;` |
| `Dark: Boolean` | `Boolean` | `__property bool Dark;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
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
procedure AddSlide(const aImageSrc: string; const aCaption: string = ''; const aDescription: string = '');
```

C++Builder

```cpp
void __fastcall AddSlide(const UnicodeString aImageSrc, const UnicodeString aCaption = '', const UnicodeString aDescription = '');
```

