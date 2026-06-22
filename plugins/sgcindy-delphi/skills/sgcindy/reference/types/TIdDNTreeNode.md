# TIdDNTreeNode

kind: class
unit: IdDNSServer

## Properties

| Delphi | Type |
| --- | --- |
| `ParentNode: TIdDNTreeNode` | `TIdDNTreeNode` |
| `CLabel: String` | `String` |
| `RRs: TIdTextModeRRs` | `TIdTextModeRRs` |
| `Children[Index[Index : Integer]: TIdDNTreeNode` | `TIdDNTreeNode` |
| `ChildIndex: TStrings` | `TStrings` |
| `AutoSortChild: Boolean` | `Boolean` |
| `FullName: string (read-only)` | `string` |
| `FundmentalClass: TIdMWayTreeNodeClass` | `TIdMWayTreeNodeClass` |

## Methods

```pascal
function AddChild : TIdDNTreeNode;
function InsertChild(Index : Integer) : TIdDNTreeNode;
procedure RemoveChild(Index : Integer);
procedure SortChildren;
procedure Clear;
procedure SaveToFile(Filename : String);
function IndexByLabel(CLabel : String): Integer;
function IndexByNode(ANode : TIdDNTreeNode) : Integer;
```

