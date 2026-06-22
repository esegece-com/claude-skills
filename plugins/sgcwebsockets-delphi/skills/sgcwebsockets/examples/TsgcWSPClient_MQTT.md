# TsgcWSPClient_MQTT - Example

Usage of `TsgcWSPClient_MQTT` extracted from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo. See the full project for context.

API reference: [TsgcWSPClient_MQTT](../reference/api/TsgcWSPClient_MQTT.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
procedure TfrmWebSocketClient.btnSubscribeMQTTClick(Sender: TObject);
  begin
  MQTT.Subscribe(txtChannelMQTT.Text);
  end;

procedure TfrmWebSocketClient.btnUnsubscribeMQTTClick(Sender: TObject);
  begin
  MQTT.Unsubscribe(txtChannelMQTT.Text);
  end;

procedure TfrmWebSocketClient.btnPublishMQTTClick(Sender: TObject);
  begin
  MQTT.Publish(txtPublishChannelMQTT.Text, txtPublishMessageMQTT.Text,
  TmqttQoS(cboQoSMQTT.itemIndex), chkRetainMQTT.Checked);
  end;

procedure TfrmWebSocketClient.btnPingMQTTClick(Sender: TObject);
  begin
  MQTT.Ping;
  end;

procedure TfrmWebSocketClient.cboServerMQTTChange(Sender: TObject);
  begin
  DoServerMQTT(cboServerMQTT.itemIndex);
  end;

MQTT.Client := nil;
MQTT.Client := WSClient;
MQTT.Authentication.Enabled := False;
MQTT.Authentication.Username := '';
MQTT.Authentication.Password := '';
procedure TfrmWebSocketClient.DoServerMQTT(aItemIndex: Integer);
  begin
  DoClear;
  MQTT.Client := WSClient;
  
  txtParameters.Text := '/';
  chkTLS.Checked := False;
  MQTT.Authentication.Enabled := False;
  MQTT.Authentication.Username := '';
  MQTT.Authentication.Password := '';
  MQTT.MQTTVersion := mqtt311;
  
  case aItemIndex of
  0: // esegece.com
  begin
  txtHost.Text := 'www.sgcwebsockets.com';
  txtPort.Text := '15675';
  txtParameters.Text := '/ws';
  MQTT.Authentication.Enabled := True;
  MQTT.Authentication.Username := 'sgc';
  MQTT.Authentication.Password := 'sgc';
  end;
  1: // test.mosquitto.org
  begin
  txtHost.Text := 'test.mosquitto.org';
  txtPort.Text := '1883';
  chkTLS.Checked := False;
  chkOverWebSocket.Checked := False;
  end;
```

