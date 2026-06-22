# TsgcHTMLNodeList

kind: class
unit: sgcHTML_Nodes

## Properties

| Delphi | Type |
| --- | --- |
| `Count: Integer (read-only)` | `Integer` |
| `Items[aIndex[aIndex: Integer]: TsgcHTMLNode (read-only)` | `TsgcHTMLNode` |
| `HTML: string (read-only)` | `string` |

## Methods

```pascal
function Add(aNode: TsgcHTMLNode): TsgcHTMLNode;
function AddRaw(const aHTML: string): TsgcHTMLRaw;
function AddText(const aText: string): TsgcHTMLText;
function AddElement(const aTag, aText: string; const aCSSClass: string = '') : TsgcHTMLContainer;
function AddScript(const aSrcOrCode: string; aIsSrc: Boolean = True) : TsgcHTMLScript;
function AddStylesheet(const aHref: string): TsgcHTMLStylesheet;
function AddMeta(const aName, aContent: string): TsgcHTMLMeta;
procedure Clear;
```

