# TsgcWSMQTTPublishExEvent

kind: event handler type
unit: sgcWebSocket_Protocol_MQTT_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; aTopic: String; aData: TsgcWSMQTTPublishData; PublishProperties: TsgcWSMQTTPUBLISHProperties; aMessage: TsgcWSMQTTMessage) of object
```

