# TsgcWSPClient_STOMP_RabbitMQ - Example

Usage of `TsgcWSPClient_STOMP_RabbitMQ` extracted from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo. See the full project for context.

API reference: [TsgcWSPClient_STOMP_RabbitMQ](../reference/api/TsgcWSPClient_STOMP_RabbitMQ.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
procedure TfrmWebSocketClient.btnSubscribeSTOMPClick(Sender: TObject);
  begin
  STOMP.SubscribeTopic(txtChannelSTOMP.Text);
  end;

procedure TfrmWebSocketClient.btnUnSubscribeSTOMPClick(Sender: TObject);
  begin
  STOMP.UnSubscribeTopic(txtChannelSTOMP.Text);
  end;

procedure TfrmWebSocketClient.btnPublishSTOMPClick(Sender: TObject);
  begin
  STOMP.PublishTopic(txtPublishChannelSTOMP.Text, txtPublishMessageSTOMP.Text);
  end;

procedure TfrmWebSocketClient.cboServerSTOMPChange(Sender: TObject);
  begin
  DoServerSTOMP(cboServerSTOMP.itemIndex);
  end;

STOMP.Client := nil;
procedure TfrmWebSocketClient.DoServerSTOMP(aItemIndex: Integer);
  begin
  DoClear;
  STOMP.Client := WSClient;
  
  txtParameters.Text := '/';
  chkTLS.Checked := False;
  STOMP.Authentication.Enabled := False;
  STOMP.Authentication.Username := '';
  STOMP.Authentication.Password := '';
  
  case aItemIndex of
  0: // esegece.com
  begin
  txtHost.Text := 'www.sgcwebsockets.com';
  txtPort.Text := '15674';
  STOMP.Authentication.Enabled := True;
  STOMP.Authentication.Username := 'sgc';
  STOMP.Authentication.Password := 'sgc';
  txtParameters.Text := '/ws';
  end;
  end;

```

