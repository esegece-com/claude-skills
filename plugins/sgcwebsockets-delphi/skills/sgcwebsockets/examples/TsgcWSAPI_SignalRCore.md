# TsgcWSAPI_SignalRCore - Example

Usage of `TsgcWSAPI_SignalRCore` extracted from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo. See the full project for context.

API reference: [TsgcWSAPI_SignalRCore](../reference/api/TsgcWSAPI_SignalRCore.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
procedure TfrmWebSocketClient.btnSignalRCoreCloseClick(Sender: TObject);
  begin
  SIGNALRCORE.Close;
  end;

procedure TfrmWebSocketClient.btnSignalRCoreSendMessageClick(Sender: TObject);
  begin
  case cboSignalRCoreServer.itemIndex of
  0:
  SIGNALRCORE.Invoke('SendMessage', [txtSignalRCoreUser.Text,
  txtSignalRCoreMessage.Text]);
  1:
  SIGNALRCORE.Invoke('Send', [txtSignalRCoreMessage.Text]);
  end;

SIGNALRCORE.Client := nil;
procedure TfrmWebSocketClient.DoServerSIGNALRCORE(aItemIndex: Integer);
  begin
  DoClear;
  SIGNALRCORE.Client := WSClient;
  case aItemIndex of
  0:
  begin
  SIGNALRCORE.SIGNALRCORE.Authentication.Enabled := False;
  SIGNALRCORE.SIGNALRCORE.Hub := '/Chathub';
  WSClient.Specifications.RFC6455 := True;
  
  txtHost.Text := 'www.esegece.com';
  txtPort.Text := '5000';
  end;
  1:
  begin
  SIGNALRCORE.SIGNALRCORE.Authentication.Enabled := True;
  SIGNALRCORE.SIGNALRCORE.Authentication.Authentication :=
  srcaRequestToken;
  SIGNALRCORE.SIGNALRCORE.Authentication.Username := 'mail@mail.com';
  SIGNALRCORE.SIGNALRCORE.Authentication.Password := 'secret';
  SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldUsername
  := 'email';
  SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldPassword :=
  'password';
  SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldToken
  := 'token';
  SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.QueryFieldToken :=
  'access_token';
  SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.URL :=
  '/account/token';
  
  SIGNALRCORE.SIGNALRCORE.Hub := '/hubs/chat';
  WSClient.Specifications.RFC6455 := True;
  
  txtHost.Text := 'www.esegece.com';
  txtPort.Text := '5001';
  end;
  end;

```

