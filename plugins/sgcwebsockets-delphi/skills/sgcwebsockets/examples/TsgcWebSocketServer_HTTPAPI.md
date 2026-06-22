# TsgcWebSocketServer_HTTPAPI - Example

Usage of `TsgcWebSocketServer_HTTPAPI` extracted from the **03.WebSocket_High_Performance_Server/01.HTTP_SYS_WebSocket_Server** demo. See the full project for context.

API reference: [TsgcWebSocketServer_HTTPAPI](../reference/api/TsgcWebSocketServer_HTTPAPI.md)
Source demo: `03.WebSocket_High_Performance_Server/01.HTTP_SYS_WebSocket_Server` (file `uServerChat.pas`)

```pascal
procedure TfrmHTTPAPIServerChat.btnStartClick(Sender: TObject);
  begin
  // ... bindings
  WSServer.Host := txtHost.Text;
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  
  // ... authentication
  if chkAuthentication.Checked then
  WSServer.Authentication.AuthUsers.Add(txtAuthUser.Text + '=' +
  txtAuthPassword.Text);
  
  // ... ssl
  WSServer.SSL := chkSSL.Checked;
  if WSServer.SSL then
  WSServer.SSLOptions.Hash := txtHash.Text;
  
  // ... active
  WSServer.Active := True;
  end;

procedure TfrmHTTPAPIServerChat.btnStopClick(Sender: TObject);
  begin
  WSServer.Active := False;
  
  if not WSServer.Active then
  begin
  memoLog.Lines.Add('#Server Stopped');
  pnlServerOptions.Enabled := True;
  end;
  end;

procedure TfrmHTTPAPIServerChat.chkAuthenticationClick(Sender: TObject);
  begin
  WSServer.Authentication.Enabled := chkAuthentication.Checked;
  end;

procedure TfrmHTTPAPIServerChat.WSServerConnect(Connection: TsgcWSConnection);
  begin
  TThread.Queue(nil,
  procedure
  begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
  end);
  end;
  
  procedure TfrmHTTPAPIServerChat.WSServerDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
  begin
  TThread.Queue(nil,
  procedure
  begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' +
  Connection.IP);
  end);
  end;
  
  procedure TfrmHTTPAPIServerChat.WSServerError(Connection: TsgcWSConnection;
  const Error: string);
  begin
  TThread.Queue(nil,
```

