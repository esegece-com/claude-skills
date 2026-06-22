# TsgcHTTP_JWT_Server - Example

Usage of `TsgcHTTP_JWT_Server` extracted from the **20.HTTP_Protocol/05.JWT** demo. See the full project for context.

API reference: [TsgcHTTP_JWT_Server](../reference/api/TsgcHTTP_JWT_Server.md)
Source demo: `20.HTTP_Protocol/05.JWT` (file `FJWT_Server.pas`)

```pascal
procedure TFRMJWTServer.DoLog(const aText: String);
  begin
  TThread.Queue(nil,
  procedure
  begin
  if Assigned(memoLog) then
  memoLog.Lines.Add(aText);
  end);
  end;
  
  procedure TFRMJWTServer.JWTServerJWTAfterValidateToken(Sender: TObject;
  aConnection: TsgcWSConnection; aToken, aHeader, aPayload, aError: string;
  var Valid: Boolean);
  begin
  if Valid then
  DoLog('#Valid JWT: ' + aHeader + ' ' + aPayload)
  else
  DoLog('#Invalid JWT: ' + aError);
  end;
  
  procedure TFRMJWTServer.JWTServerJWTException(Sender: TObject; aConnection:
  TsgcWSConnection; E: Exception);
  begin
  DoLog('#exception: ' + E.Message);
  end;
  
  procedure TFRMJWTServer.serverCommandGet(AContext: TIdContext; ARequestInfo:
  TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
  begin
  AResponseInfo.ResponseNo := 200;
  AResponseInfo.ContentType := ARequestInfo.ContentType;
  AResponseInfo.ContentText := '<html><head><title>sgcWebSockets JWT Server</title></head><body>JWT Test Page.</body></html>';
  end;
  
  procedure TFRMJWTServer.serverConnect(Connection: TsgcWSConnection);
  begin
  Connection.WriteData('JWT Token Successful');
  end;
  
  procedure TFRMJWTServer.serverShutdown(Sender: TObject);
  begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;
  
  procedure TFRMJWTServer.serverStartup(Sender: TObject);
  begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;
  
  end.

```

