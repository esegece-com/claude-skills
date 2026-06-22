# TsgcSTUNClient - Example

Usage of `TsgcSTUNClient` extracted from the **35.P2P/02.STUN** demo. See the full project for context.

API reference: [TsgcSTUNClient](../reference/api/TsgcSTUNClient.md)
Source demo: `35.P2P/02.STUN` (file `FSTUNClient.pas`)

```pascal
procedure TFRMSTUNClient.btnRequestBindingClick(Sender: TObject);
  begin
  // stun server
  stun_client.Host := txtHost.Text;
  stun_client.Port := StrToInt(txtPort.Text);
  case cboTransport.ItemIndex of
  0:
  stun_client.Transport := stunUDP;
  1:
  stun_client.Transport := stunTCP;
  end;

stun_client.RetransmissionOptions.Enabled := chkRetransmissions.Checked;
stun_client.RetransmissionOptions.RTO := StrToInt(txtRTO.Text);
stun_client.RetransmissionOptions.MaxRetries := StrToInt(txtMaxRetries.Text);
stun_client.STUNOptions.Authentication.Credentials := stauLongTermCredential;
stun_client.STUNOptions.Fingerprint := True;
stun_client.STUNOptions.Authentication.Credentials := stauNone;
stun_client.STUNOptions.Fingerprint := False;
stun_client.STUNOptions.Authentication.Username := txtUsername.Text;
stun_client.STUNOptions.Authentication.Password := txtPassword.Text;
```

