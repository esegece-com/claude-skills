# TsgcWebSocketClient - Example

Usage of `TsgcWebSocketClient` extracted from the **01.WebSocket_Quick_Start/01.Server_and_Client_Chat** demo. See the full project for context.

API reference: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)
Source demo: `01.WebSocket_Quick_Start/01.Server_and_Client_Chat` (file `uClientChat.pas`)

```pascal
procedure TfrmClientChat.btnSendClick(Sender: TObject);
  begin
  if WSClient.Active then
  begin
  if txtName.Text = '' then
  raise Exception.Create('Type a Name before send a message');
  
  if txtMessage.Text = '' then
  raise Exception.Create('Type a Message before send a message');
  
  WSClient.WriteData(txtName.Text + ': ' + txtMessage.Text);
  
  txtMessage.Text := '';
  end
  else
  raise Exception.Create('Not connected');
  end;

procedure TfrmClientChat.btnStartClick(Sender: TObject);
  begin
  WSClient.Authentication.Enabled := chkAuthentication.Checked;
  if WSClient.Authentication.Enabled then
  begin
  WSClient.Authentication.User := txtAuthUser.Text;
  WSClient.Authentication.Password := txtAuthPassword.Text;
  end;
  
  if chkTLS.Checked then
  WSClient.Port := StrToInt(txtSSLPort.Text)
  else
  WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;
  
  case cboOpenSSLAPI.ItemIndex of
  0:
  begin
  WSClient.TLSOptions.IOHandler := iohOpenSSL;
  WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_1_0;
  end;
  1:
  begin
  WSClient.TLSOptions.IOHandler := iohOpenSSL;
  WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
  end;
  2:
  begin
  WSClient.TLSOptions.IOHandler := iohOpenSSL;
  WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  end;
  3:
  WSClient.TLSOptions.IOHandler := iohSChannel
  end;

WSClient.TLSOptions.Version := tlsUndefined;
WSClient.TLSOptions.Version := tls1_0;
WSClient.TLSOptions.Version := tls1_1;
WSClient.TLSOptions.Version := tls1_2;
WSClient.TLSOptions.Version := tls1_3;
WSClient.TLS := chkTLS.Checked;
WSClient.Proxy.Enabled := chkProxy.Checked;
```

