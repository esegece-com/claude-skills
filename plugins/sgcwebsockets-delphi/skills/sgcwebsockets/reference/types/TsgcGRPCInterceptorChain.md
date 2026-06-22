# TsgcGRPCInterceptorChain

kind: class
unit: sgcGRPC_Interceptors

## Methods

```pascal
procedure Add(aInterceptor: TsgcGRPCInterceptor);
procedure Remove(aInterceptor: TsgcGRPCInterceptor);
procedure Clear;
function Count: Integer;
function GetInterceptor(aIndex: Integer): TsgcGRPCInterceptor;
procedure ExecuteBeforeUnaryCall(const aContext : TsgcGRPCInterceptorContext);
procedure ExecuteAfterUnaryCall(const aContext: TsgcGRPCInterceptorContext; const aResponse: TsgcGRPCResponse);
procedure ExecuteBeforeStreamOpen(const aContext : TsgcGRPCInterceptorContext);
procedure ExecuteOnStreamMessage(const aContext: TsgcGRPCInterceptorContext; const aMessage: TsgcGRPCStreamMessage);
procedure ExecuteAfterStreamClose(const aContext : TsgcGRPCInterceptorContext; aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string);
procedure ExecuteOnError(const aContext: TsgcGRPCInterceptorContext; aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string);
```

