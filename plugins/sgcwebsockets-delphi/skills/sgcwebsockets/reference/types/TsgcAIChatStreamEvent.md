# TsgcAIChatStreamEvent

kind: event handler type
unit: sgcAI_Chat

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChunk: string; var Cancel: Boolean) of object
```

