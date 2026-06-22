# TsgcTURNBeforeRelayChannelDataEvent

kind: event handler type
unit: sgcP2P_TURN_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; aRelayType: TsgcTURNRelayChannelDataType; const aPeerIP: string; aPeerPort: Word; const aChannelData: TsgcTURNChannelData; var Accept: Boolean) of object
```

