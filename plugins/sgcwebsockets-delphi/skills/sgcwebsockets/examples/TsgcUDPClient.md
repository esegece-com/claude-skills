# TsgcUDPClient - Example

Usage of `TsgcUDPClient` extracted from the **35.P2P/01.UDP_Server_Client** demo. See the full project for context.

API reference: [TsgcUDPClient](../reference/api/TsgcUDPClient.md)
Source demo: `35.P2P/01.UDP_Server_Client` (file `FUDP_Client.pas`)

```pascal
procedure TFRMUDP_Client.btnSendMessageClick(Sender: TObject);
  begin
  if txtMessage.Text <> '' then
  begin
  client.Host := txtHost.Text;
  client.Port := StrToInt(txtPort.Text);
  
  client.DTLS := chkDTLS.Checked;
  client.DTLSOptions.CertFile := txtCertFile.Text;
  client.DTLSOptions.KeyFile := txtKeyFile.Text;
  client.DTLSOptions.RootCertFile := txtRootCertFile.Text;
  
  client.WriteData(txtMessage.Text);
  
  txtMessage.Text := '';
  end;
  end;

```

