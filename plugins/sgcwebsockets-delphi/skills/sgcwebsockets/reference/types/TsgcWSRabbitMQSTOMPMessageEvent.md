# TsgcWSRabbitMQSTOMPMessageEvent

kind: event handler type
unit: sgcWebSocket_Protocol_STOMP_RabbitMQ_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; MessageText: String; Headers: TsgcWSRabbitMQSTOMPHeadersMessage; Subscription: TsgcWSBrokerSTOMPSubscriptionItem) of object
```

