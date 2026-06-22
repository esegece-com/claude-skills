# TsgcSTUNServer - Example

Usage of `TsgcSTUNServer` extracted from the **35.P2P/02.STUN** demo. See the full project for context.

API reference: [TsgcSTUNServer](../reference/api/TsgcSTUNServer.md)
Source demo: `35.P2P/02.STUN` (file `FSTUNServer.pas`)

```pascal
procedure TFRMSTUNServer.btnStartClick(Sender: TObject);
  begin
  if stun_server.Active then
  stun_server.Active := False;
  
  // only for update memo, production let the value neNoSync
  stun_server.NotifyEvents := neAsynchronous;
  
  // initialize server
  stun_server.Host := txtHost.Text;
  stun_server.Port := StrToInt(txtPort.Text);
  // bindings
  stun_server.Bindings.Clear;
  With stun_server.Bindings.Add do
  begin
  IP := txtHost.Text;
  Port := StrToInt(txtPort.Text);
  end;
  // long term credentials
  stun_server.STUNOptions.Authentication.Enabled := chkLongTermCredentials.Checked;
  stun_server.STUNOptions.Authentication.LongTermCredentials.Enabled := chkLongTermCredentials.Checked;
  
  stun_server.Active := True;
  
  DoLog('#start server');
  end;

procedure TFRMSTUNServer.btnStopClick(Sender: TObject);
  begin
  stun_server.Active := False;
  
  DoLog('#stop server');
  end;

```

