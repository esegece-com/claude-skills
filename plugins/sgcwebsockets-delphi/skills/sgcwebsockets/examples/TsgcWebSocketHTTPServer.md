# TsgcWebSocketHTTPServer - Example

Usage of `TsgcWebSocketHTTPServer` extracted from the **01.WebSocket_Quick_Start/01.Server_and_Client_Chat** demo. See the full project for context.

API reference: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)
Source demo: `01.WebSocket_Quick_Start/01.Server_and_Client_Chat` (file `uServerChat.pas`)

```pascal
procedure TfrmServerChat.FormCreate(Sender: TObject);
  begin
  btnStart.Click;
  WSServer.DocumentRoot := ExtractFilePath(Application.ExeName);
  end;

procedure TfrmServerChat.btnStartClick(Sender: TObject);
  begin
  if chkSSL.Checked then
  WSServer.Port := StrToInt(txtSSLPort.Text)
  else
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  
  // ... bindings
  With WSServer.Bindings.Add do
  begin
  Port := StrToInt(txtDefaultPort.Text);
  IP := txtHost.Text;
  end;
  
  WSServer.HTTP2Options.Enabled := chkHTTP2.Checked;
  if WSServer.HTTP2Options.Enabled then
  begin
  WSServer.SSLOptions.IOHandler := iohOpenSSL;
  WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
  WSServer.SSLOptions.Version := tls1_3;
  end
  else
  begin
  case cboOpenSSLAPI.ItemIndex of
  0:
  begin
  WSServer.SSLOptions.IOHandler := iohOpenSSL;
  WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_0;
  end;
  1:
  begin
  WSServer.SSLOptions.IOHandler := iohOpenSSL;
  WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
  end;
  2:
  begin
  WSServer.SSLOptions.IOHandler := iohOpenSSL;
  WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  end;
  3:
  WSServer.SSLOptions.IOHandler := iohSChannel;
  end;
  if cboOpenSSLAPI.ItemIndex = 3 then
  begin
  WSServer.SSLOptions.CertFile := 'sgc_schannel.pfx';
  WSServer.SSLOptions.KeyFile := '';
  WSServer.SSLOptions.RootCertFile := '';
  WSServer.SSLOptions.Password := '1234';
  end
  else
  begin
  WSServer.SSLOptions.CertFile := 'sgc.pem';
  WSServer.SSLOptions.KeyFile := 'sgc.pem';
  WSServer.SSLOptions.RootCertFile := 'sgc.pem';
```

