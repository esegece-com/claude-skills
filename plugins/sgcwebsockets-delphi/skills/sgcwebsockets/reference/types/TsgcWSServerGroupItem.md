# TsgcWSServerGroupItem

kind: class
unit: sgcWebSocket_Server_Groups

## Properties

| Delphi | Type |
| --- | --- |
| `Clients: TsgcWSServerGroups_Clients` | `TsgcWSServerGroups_Clients` |
| `ID: String` | `String` |
| `Order: Int64` | `Int64` |

## Methods

```pascal
function Add(const aConnection: TsgcWSConnection): Boolean;
function Remove(const aConnection: TsgcWSConnection): Boolean;
procedure BroadCast(const aMessage: string);
```

