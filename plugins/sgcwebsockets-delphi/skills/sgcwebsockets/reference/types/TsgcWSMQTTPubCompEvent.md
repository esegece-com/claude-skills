# TsgcWSMQTTPubCompEvent

kind: event handler type
unit: sgcWebSocket_Protocol_MQTT_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: String; PubCompProperties: TsgcWSMQTTPUBCOMPProperties) of object
```

