# TsgcWSMQTTConnectEvent

kind: event handler type
unit: sgcWebSocket_Protocol_MQTT_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const Session: Boolean; const ReasonCode: Integer; const ReasonName: String; const ConnectProperties: TsgcWSMQTTCONNACKProperties) of object
```

