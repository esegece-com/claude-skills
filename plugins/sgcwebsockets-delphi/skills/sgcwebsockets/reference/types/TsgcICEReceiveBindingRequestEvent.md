# TsgcICEReceiveBindingRequestEvent

kind: event handler type
unit: sgcP2P_ICE_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aBinding: TsgcICE_Binding; const aMessage: TsgcSTUN_Message; var Accept: Boolean) of object
```

