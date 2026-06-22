# TsgcWSPServer_WAMP - Example

Usage of `TsgcWSPServer_WAMP` extracted from the **02.WebSocket_Protocols/04.WAMP_Protocol** demo. See the full project for context.

API reference: [TsgcWSPServer_WAMP](../reference/api/TsgcWSPServer_WAMP.md)
Source demo: `02.WebSocket_Protocols/04.WAMP_Protocol` (file `uServerWAMP.pas`)

```pascal
procedure TfrmServerWAMP.DoCall(const CallId, ProcURI, Arguments: string);
  var
  vInteger: Integer;
  oThread: TTimerThread;
  begin
  if ProcURI = 'sgc:calculate' then
  begin
  TryStrToInt(Arguments, vInteger);
  WSPWAMP.CallResult(CallId, IntToStr(vInteger * 50));
  end
  else if ProcURI = 'sgc:timer' then
  begin
  oThread := TTimerThread.Create(True);
  oThread.FreeOnTerminate := True;
  oThread.CallId := CallId;
  oThread.Protocol := WSPWAMP;
  oThread.Start;
  end
  else
  WSPWAMP.CallError(CallId, ProcURI, 'Call method not found!');
  end;

```

