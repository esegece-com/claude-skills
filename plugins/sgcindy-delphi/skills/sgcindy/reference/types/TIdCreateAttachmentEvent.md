# TIdCreateAttachmentEvent

kind: event handler type
unit: IdMessage

A handler assigned to this event must match this signature:

```pascal
procedure(const AMsg: TIdMessage; const AHeaders: TStrings; var AAttachment: TIdAttachment) of object
```

