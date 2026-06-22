# TsgcFirewallOnResolveBot

kind: event handler type
unit: sgcWebSocket_Server_Firewall

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aIP: string; var aClassification: TsgcBotClassification; var aBotName: string) of object
```

