# TsgcOnAWSSQSError

kind: event handler type
unit: sgcHTTP_Amazon_SQS

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Error_Code, Error_Description, RawError: String) of object
```

