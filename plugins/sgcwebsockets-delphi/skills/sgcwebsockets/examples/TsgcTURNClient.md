# TsgcTURNClient - Example

Usage of `TsgcTURNClient` extracted from the **35.P2P/03.TURN** demo. See the full project for context.

API reference: [TsgcTURNClient](../reference/api/TsgcTURNClient.md)
Source demo: `35.P2P/03.TURN` (file `FTURNClient.pas`)

```pascal
procedure TFRMSTUNClient.btnSTUNRequestBindingClick(Sender: TObject);
  begin
  DoInitialize;
  // send request binding
  turn_client.SendRequest;
  end;

procedure TFRMSTUNClient.btnTURNAllocateClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.Allocate;
  end;

procedure TFRMSTUNClient.btnTURNChannelBindClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.ChannelBind(txtTURNChannelBindPeerAddress.Text,
  StrToInt(txtTURNChannelBindPeerPort.Text));
  end;

procedure TFRMSTUNClient.btnTURNCreatePermissionClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.CreatePermission(txtTURNCreatePermissionPeer.Text);
  end;

procedure TFRMSTUNClient.btnTURNRefreshClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.Refresh(StrToInt(txtTURNRefreshLifetime.Text));
  end;

procedure TFRMSTUNClient.btnTURNSendChannelDataClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.SendChannelData(StrToInt(txtTURNSendChannelDataChannelId.Text),
  txtTURNSendChannelDataChannelData.Text);
  end;

procedure TFRMSTUNClient.btnTURNSendIndicationClick(Sender: TObject);
  begin
  DoInitialize;
  turn_client.SendIndication(txtTURNSendIndicationPeerAddress.Text,
  StrToInt(txtTURNSendIndicationPeerPort.Text),
  txtTURNSendIndicationData.Text);
  end;

turn_client.Host := txtHost.Text;
turn_client.Port := StrToInt(txtPort.Text);
turn_client.RetransmissionOptions.Enabled := chkRetransmissions.Checked;
turn_client.RetransmissionOptions.RTO := StrToInt(txtRTO.Text);
turn_client.RetransmissionOptions.MaxRetries := StrToInt(txtMaxRetries.Text);
turn_client.STUNOptions.Authentication.Credentials := stauNone;
turn_client.TURNOptions.Authentication.Credentials :=
turn_client.TURNOptions.Fingerprint := True;
turn_client.TURNOptions.Authentication.Credentials := stauNone;
turn_client.TURNOptions.Fingerprint := False;
turn_client.TURNOptions.Authentication.Username := txtUsername.Text;
turn_client.TURNOptions.Authentication.Password := txtPassword.Text;
```

