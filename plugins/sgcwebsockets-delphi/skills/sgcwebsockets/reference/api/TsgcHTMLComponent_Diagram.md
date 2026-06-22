# TsgcHTMLComponent_Diagram

unit: sgcHTML_Component_Diagram
Edition: All-Access

Add `sgcHTML_Component_Diagram` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Nodes: TsgcHTMLDiagramNodes` | [TsgcHTMLDiagramNodes](../types/TsgcHTMLDiagramNodes.md) | `__property TsgcHTMLDiagramNodes * Nodes;` |
| `Connections: TsgcHTMLDiagramConnections` | [TsgcHTMLDiagramConnections](../types/TsgcHTMLDiagramConnections.md) | `__property TsgcHTMLDiagramConnections * Connections;` |
| `DiagramID: string` | `string` | `__property UnicodeString DiagramID;` |
| `DiagramWidth: Integer` | `Integer` | `__property int DiagramWidth;` |
| `DiagramHeight: Integer` | `Integer` | `__property int DiagramHeight;` |
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
function AddNode(const aID, aText: string; aX, aY: Integer; aColor: TsgcHTMLColor = hcPrimary; aShape: TsgcHTMLDiagramNodeShape = nsRoundedRect): TsgcHTMLDiagramNode;
procedure Connect(const aFromID, aToID: string; const aLabel_: string = '');
```

C++Builder

```cpp
TsgcHTMLDiagramNode * __fastcall AddNode(const UnicodeString aID, const UnicodeString aText, int aX, int aY, TsgcHTMLColor * aColor = hcPrimary, TsgcHTMLDiagramNodeShape * aShape = nsRoundedRect);
void __fastcall Connect(const UnicodeString aFromID, const UnicodeString aToID, const UnicodeString aLabel_ = '');
```

