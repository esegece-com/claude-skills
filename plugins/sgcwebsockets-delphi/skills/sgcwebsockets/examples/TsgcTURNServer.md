# TsgcTURNServer - Example

Usage of `TsgcTURNServer` extracted from the **35.P2P/03.TURN** demo. See the full project for context.

API reference: [TsgcTURNServer](../reference/api/TsgcTURNServer.md)
Source demo: `35.P2P/03.TURN` (file `FTURNServer.pas`)

```pascal
procedure TFRMTURNServer.btnStartClick(Sender: TObject);
  begin
  if turn_server.Active then
  turn_server.Active := False;
  
  // only for update memo, production let the value neNoSync
  turn_server.NotifyEvents := neAsynchronous;
  
  // initialize server
  turn_server.Host := txtHost.Text;
  turn_server.Port := StrToInt(txtPort.Text);
  // bindings
  turn_server.Bindings.Clear;
  With turn_server.Bindings.Add do
  begin
  IP := txtHost.Text;
  Port := StrToInt(txtPort.Text);
  end;
  // stun options
  turn_server.STUNOptions.Authentication.Enabled := False;
  
  // turn options
  turn_server.TURNOptions.Authentication.Enabled :=
  chkLongTermCredentials.Checked;
  turn_server.TURNOptions.Authentication.LongTermCredentials.Enabled :=
  chkLongTermCredentials.Checked;
  turn_server.TURNOptions.Authentication.LongTermCredentials.Realm :=
  txtRealm.Text;
  
  turn_server.Active := True;
  
  DoLog('#start server');
  end;

procedure TFRMTURNServer.btnStopClick(Sender: TObject);
  begin
  turn_server.Active := False;
  
  DoLog('#stop server');
  end;

procedure TFRMTURNServer.turn_serverSTUNRequestAuthorization(Sender: TObject;
  const aRequest: TsgcSTUN_Message; const aUsername, aRealm: string;
  var Password: string);
  begin
  if (aUsername = txtUsername.Text) and
  (aRealm = turn_server.TURNOptions.Authentication.LongTermCredentials.Realm)
  then
  Password := txtPassword.Text;
  end;

```

