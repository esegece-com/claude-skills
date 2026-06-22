# TsgcWSPClient_Presence - Example

Usage of `TsgcWSPClient_Presence` extracted from the **02.WebSocket_Protocols/03.Presence_Protocol** demo. See the full project for context.

API reference: [TsgcWSPClient_Presence](../reference/api/TsgcWSPClient_Presence.md)
Source demo: `02.WebSocket_Protocols/03.Presence_Protocol` (file `FPresenceClient.pas`)

```pascal
procedure TForm16.btnConnectClick(Sender: TObject);
  begin
  Log.Lines.clear;
  
  Client.Host := txtHost.Text;
  Client.Port := StrToInt(txtPort.Text);
  PresenceClient.Presence.Name := cboMembers.Text;
  PresenceClient.EncodeBase64 := chkBase64.Checked;
  Client.Active := True;
  end;

procedure TForm16.btnPublishClick(Sender: TObject);
  begin
  if cboChannels.ItemIndex > 0 then
  PresenceClient.Publish(txtMessage.Text + ' of ' + cboChannels.Text, cboChannels.Text)
  else
  PresenceClient.Publish(txtMessage.Text);
  end;

procedure TForm16.btnSubscribeClick(Sender: TObject);
  begin
  if cboChannels.ItemIndex > 0 then
  PresenceClient.Subscribe(cboChannels.Text);
  end;

procedure TForm16.btnUnsubscribeClick(Sender: TObject);
  begin
  if cboChannels.ItemIndex > 0 then
  PresenceClient.Unsubscribe(cboChannels.Text);
  end;

procedure TForm16.btnGetMembersClick(Sender: TObject);
  begin
  PresenceClient.GetMembers;
  end;

procedure TForm16.btnInviteClick(Sender: TObject);
  begin
  PresenceClient.Invite(cboChannels.Text, txtInviteId.Text);
  end;

```

