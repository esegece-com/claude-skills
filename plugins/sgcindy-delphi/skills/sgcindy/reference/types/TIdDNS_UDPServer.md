# TIdDNS_UDPServer

kind: class
unit: IdDNSServer

## Properties

| Delphi | Type |
| --- | --- |
| `RootDNS_NET: TStrings` | `TStrings` |
| `Cached_Tree: TIdDNTreeNode (read-only)` | [TIdDNTreeNode](./TIdDNTreeNode.md) |
| `Handed_Tree: TIdDNTreeNode (read-only)` | [TIdDNTreeNode](./TIdDNTreeNode.md) |
| `Busy: Boolean (read-only)` | `Boolean` |
| `GlobalCS: TIdCriticalSection (read-only)` | [TIdCriticalSection](./TIdCriticalSection.md) |
| `DefaultPort: TIdPort` | `TIdPort` |
| `AutoLoadMasterFile: Boolean` | `Boolean` |
| `ZoneMasterFiles: TStrings` | `TStrings` |
| `CacheUnknowZone: Boolean` | `Boolean` |
| `Handed_DomainList: TStrings` | `TStrings` |
| `DNSVersion: string` | `string` |
| `offerDNSVersion: Boolean` | `Boolean` |
| `ThreadClass: TIdUDPListenerThreadClass` | [TIdUDPListenerThreadClass](./TIdUDPListenerThreadClass.md) |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](./TIdSocketHandles.md) |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](./TIdReuseSocket.md) |
| `ThreadedEvent: boolean` | `boolean` |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](./TIdSocketHandle.md) |
| `ReceiveTimeout: Integer` | `Integer` |
| `Active: Boolean` | `Boolean` |
| `BufferSize: Integer` | `Integer` |
| `BroadcastEnabled: Boolean` | `Boolean` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](./TIdIPVersion.md) |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnBeforeQuery: TIdDNSBeforeQueryEvent` | [TIdDNSBeforeQueryEvent](./TIdDNSBeforeQueryEvent.md) |
| `OnAfterQuery: TIdDNSAfterQueryEvent` | [TIdDNSAfterQueryEvent](./TIdDNSAfterQueryEvent.md) |
| `OnAfterSendBack: TIdDNSAfterQueryEvent` | [TIdDNSAfterQueryEvent](./TIdDNSAfterQueryEvent.md) |
| `OnAfterCacheSaved: TIdDNSAfterCacheSaved` | [TIdDNSAfterCacheSaved](./TIdDNSAfterCacheSaved.md) |
| `OnBeforeBind: TIdSocketHandleEvent` | [TIdSocketHandleEvent](./TIdSocketHandleEvent.md) |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` |
| `OnUDPRead: TUDPReadEvent` | [TUDPReadEvent](./TUDPReadEvent.md) |
| `OnUDPException: TIdUDPExceptionEvent` | [TIdUDPExceptionEvent](./TIdUDPExceptionEvent.md) |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
function AXFR(Header : TDNSHeader; Question : string; var Answer : TIdBytes) : string;
function CompleteQuery(DNSHeader: TDNSHeader; Question: string; OriginalQuestion: TIdBytes; var Answer : TIdBytes; QType, QClass : UInt16; DNSResolver : TIdDNSResolver) : string;
function LoadZoneFromMasterFile(MasterFileName : String) : boolean;
function LoadZoneStrings(FileStrings: TStrings; Filename : String; TreeRoot : TIdDNTreeNode): Boolean;
function SearchTree(Root : TIdDNTreeNode; QName : String; QType : UInt16): TIdDNTreeNode;
procedure UpdateTree(TreeRoot : TIdDNTreeNode; RR : TIdTextModeResourceRecord);
function FindNodeFullName(Root : TIdDNTreeNode; QName : String; QType : UInt16) : string;
function FindHandedNodeByName(QName : String; QType : UInt16) : TIdDNTreeNode;
procedure Broadcast(const AData: string; const APort: TIdPort; const AIP: String = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
function ReceiveBuffer(var ABuffer : TIdBytes; var VPeerIP: string; var VPeerPort: TIdPort; AMSec: Integer = IdTimeoutDefault): integer;
function ReceiveString(const AMSec: Integer = IdTimeoutDefault; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure Send(const AHost: string; const APort: TIdPort; const AData: string; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure SendBuffer(const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion; const ABuffer : TIdBytes);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

