# TsgcHTTP2Client - Example

Usage of `TsgcHTTP2Client` extracted from the **20.HTTP_Protocol/01.HTTP2_Server_And_Client** demo. See the full project for context.

API reference: [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)
Source demo: `20.HTTP_Protocol/01.HTTP2_Server_And_Client` (file `FHTTP2_Client.pas`)

```pascal
procedure TFRMHTTP2_Client.btnExecuteRequestClick(Sender: TObject);
  var
  oSource: TStringStream;
  begin
  if not Assigned(FClient_Request) then
  begin
  FClient_Request := TsgcHTTP2Client.Create(self);
  FClient_Request.OnHTTP2Connect := OnHTTP2ConnectEvent;
  FClient_Request.OnHTTP2Disconnect := OnHTTP2DisconnectEvent;
  FClient_Request.OnHTTP2Exception := OnHTTP2ExceptionEvent;
  FClient_Request.OnHTTP2Response := OnHTTP2ResponseEvent;
  end;
  
  // wait the client has disconnected to avoid thread error
  While FClient_Request.Active do
  sleep(1);
  
  case cboMethod.ItemIndex of
  0:
  begin
  memoResponseBody.Lines.Text := FClient_Request.Get(txtURL.Text);
  memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
  FClient_Request.Disconnect;
  end;
  1:
  begin
  oSource := TStringStream.Create(memoRequest.Lines.Text);
  Try
  memoResponseBody.Lines.Text := FClient_Request.Post(txtURL.Text, oSource);
  memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
  FClient_Request.Disconnect;
  Finally
  oSource.Free;
  memoRequest.Lines.Clear;
  end;
  end;

memoResponseBody.Lines.Text := FClient_Request.Put(txtURL.Text, oSource);
memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
memoResponseBody.Lines.Text := FClient_Request.Patch(txtURL.Text, oSource);
memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
procedure TFRMHTTP2_Client.DoGoLatencyHTTP2(const aLatency: Integer);
  var
  x, y: Integer;
  vCachebust: string;
  begin
  imgGophertiles.Picture.Graphic := nil;
  if Assigned(FClient_Latency) then
  FClient_Latency.Active := False;
  FClient_Latency := TsgcHTTP2Client.Create(self);
  FClient_Latency.OnHTTP2Response := OnLatencyHTTP2ResponseEvent;
  FClient_Latency.OnHTTP2PendingRequests := OnLatencyHTTP2PendingRequests;
  FClient_Latency.Request.Accept := 'image/*,*/*;q=0.8';
  FClient_Latency.WatchDog.Enabled := True;
  vCacheBust := FormatDateTime('yyyymmddhhnnsszzz', Now);
  for y := 0 to 11 do
  begin
  for x := 0 to 14 do
  FClient_Latency.GetAsync(GetLatencyServerURL + '/gophertiles?x=' + IntToStr(x) + '&y=' + IntToStr(y) + '&cachebust=' + vCachebust + '&latency=' + IntToStr(aLatency));
  end;
```

