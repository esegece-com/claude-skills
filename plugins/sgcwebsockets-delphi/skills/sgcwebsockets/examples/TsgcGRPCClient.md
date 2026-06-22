# TsgcGRPCClient - Example

Usage of `TsgcGRPCClient` extracted from the **21.GRPC/01.GRPC_Client** demo. See the full project for context.

API reference: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md)
Source demo: `21.GRPC/01.GRPC_Client` (file `FGRPCClient.pas`)

```pascal
procedure TFrmGRPCClient.FormCreate(Sender: TObject);
  begin
  FHTTP2Client := nil;
  FGRPCClient := nil;
  FClientStreamId := 0;
  FBidiStreamId := 0;
  FLogInterceptor := nil;
  FTimeoutInterceptor := nil;
  FMetaInterceptor := nil;
  FLoadBalancer := nil;
  FHealthClient := nil;
  FReflectionClient := nil;
  end;

FGRPCClient := TsgcGRPCClient.Create(nil);
FGRPCClient.Client := GetHTTP2Client;
FGRPCClient.OnGRPCConnect := OnGRPCConnectEvent;
FGRPCClient.OnGRPCDisconnect := OnGRPCDisconnectEvent;
FGRPCClient.OnGRPCResponse := OnGRPCResponseEvent;
FGRPCClient.OnGRPCStreamMessage := OnGRPCStreamMessageEvent;
FGRPCClient.OnGRPCStreamEnd := OnGRPCStreamEndEvent;
FGRPCClient.OnGRPCError := OnGRPCErrorEvent;
FGRPCClient.OnGRPCException := OnGRPCExceptionEvent;
FGRPCClient.OnGRPCBeforeRequest := OnGRPCBeforeRequestEvent;
```

