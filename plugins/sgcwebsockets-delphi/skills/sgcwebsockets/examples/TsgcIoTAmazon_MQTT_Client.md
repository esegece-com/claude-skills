# TsgcIoTAmazon_MQTT_Client - Example

Usage of `TsgcIoTAmazon_MQTT_Client` extracted from the **10.IoT_Clients** demo. See the full project for context.

API reference: [TsgcIoTAmazon_MQTT_Client](../reference/api/TsgcIoTAmazon_MQTT_Client.md)
Source demo: `10.IoT_Clients` (file `FsgcClientIoT.pas`)

```pascal
procedure TFRMSGCClientIoT.btnAmazonConnectClick(Sender: TObject);
  begin
  AmazonIoT.Amazon.Endpoint := txtAmazonEndpoint.Text;
  AmazonIoT.Amazon.ClientId := txtAmazonClientId.Text;
  
  AmazonIoT.Certificate.Enabled := False;
  AmazonIoT.SignatureV4.Enabled := False;
  AmazonIoT.CustomAuthentication.Enabled := False;
  case cboAmazonAuthentication.ItemIndex of
  0:
  begin
  AmazonIoT.Certificate.Enabled := True;
  AmazonIoT.Certificate.CertFile := txtAmazonCertfile.Text;
  AmazonIoT.Certificate.KeyFile := txtAmazonKeyFile.Text;
  end;
  1:
  begin
  AmazonIoT.SignatureV4.Enabled := True;
  AmazonIoT.SignatureV4.Region := txtAmazonRegion.Text;
  AmazonIoT.SignatureV4.AccessKey := txtAmazonAccessKey.Text;
  AmazonIoT.SignatureV4.SecretKey := txtAmazonSecretKey.Text;
  AmazonIoT.SignatureV4.SessionToken := txtAmazonSessionToken.Text;
  end;
  2:
  begin
  AmazonIoT.CustomAuthentication.Enabled := True;
  AmazonIoT.CustomAuthentication.Parameters := txtAmazonParameters.Text;
  AmazonIoT.CustomAuthentication.Headers.Text := txtAmazonHeaders.Text;
  AmazonIoT.CustomAuthentication.WebSockets :=
  chkAmazonWebSockets.Checked;
  end;
  end;

AmazonIoT.Active := True;
procedure TFRMSGCClientIoT.btnAmazonDisconnectClick(Sender: TObject);
  begin
  AmazonIoT.Active := False;
  end;

procedure TFRMSGCClientIoT.btnPublishAmazonClick(Sender: TObject);
  begin
  case cboQoSAmazon.ItemIndex of
  0:
  AmazonIoT.Publish(txtPublishChannelAmazon.Text,
  txtPublishMessageAmazon.Text, awsIoTQoS0);
  1:
  AmazonIoT.Publish(txtPublishChannelAmazon.Text,
  txtPublishMessageAmazon.Text, awsIoTQoS1);
  end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClick(Sender: TObject);
  begin
  AmazonIoT.Subscribe(txtChannelAmazon.Text);
  end;

procedure TFRMSGCClientIoT.btnUnsubscribeAmazonClick(Sender: TObject);
  begin
  AmazonIoT.UnSubscribe(txtChannelAmazon.Text);
  end;

```

