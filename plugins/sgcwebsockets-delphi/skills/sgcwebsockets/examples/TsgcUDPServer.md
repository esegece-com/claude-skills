# TsgcUDPServer - Example

Usage of `TsgcUDPServer` extracted from the **35.P2P/01.UDP_Server_Client** demo. See the full project for context.

API reference: [TsgcUDPServer](../reference/api/TsgcUDPServer.md)
Source demo: `35.P2P/01.UDP_Server_Client` (file `FUDP_Server.pas`)

```pascal
procedure TFRMUDPServer.btnStartClick(Sender: TObject);
  begin
  // ... bindings
  server.Port := StrToInt(txtDefaultPort.Text);
  server.Bindings.Clear;
  With server.Bindings.Add do
  begin
  Port := StrToInt(txtDefaultPort.Text);
  IP := txtHost.Text;
  end;
  
  // ... dtls
  server.DTLS := chkDTLS.Checked;
  server.DTLSOptions.CertFile := txtCertFile.Text;
  server.DTLSOptions.KeyFile := txtKeyFile.Text;
  server.DTLSOptions.RootCertFile := txtRootCertFile.Text;
  
  // ... active
  server.Active := True;
  end;

procedure TFRMUDPServer.btnStopClick(Sender: TObject);
  begin
  server.Active := False;
  end;

procedure TFRMUDPServer.serverShutdown(Sender: TObject);
  begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;

procedure TFRMUDPServer.serverStartup(Sender: TObject);
  begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;

```

