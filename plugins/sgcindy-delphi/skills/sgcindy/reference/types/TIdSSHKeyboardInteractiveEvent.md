# TIdSSHKeyboardInteractiveEvent

kind: event handler type
unit: IdSSHClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aName, aInstruction: string; aPrompts: TStrings; aEchos: TList; aResponses: TStrings) of object
```

