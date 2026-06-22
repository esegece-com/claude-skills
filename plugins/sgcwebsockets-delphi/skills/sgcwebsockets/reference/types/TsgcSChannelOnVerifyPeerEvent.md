# TsgcSChannelOnVerifyPeerEvent

kind: event handler type
unit: sgcSSL_SChannel_Indy

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aContext: TsgcSChannelContext; aError: TsgcSChannelVerifyError; var Accept: Boolean) of object
```

