# TsgcWSAPI_Pusher - Example

Usage of `TsgcWSAPI_Pusher` extracted from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo. See the full project for context.

API reference: [TsgcWSAPI_Pusher](../reference/api/TsgcWSAPI_Pusher.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
procedure TfrmWebSocketClient.btnPublishPUSHERClick(Sender: TObject);
  begin
  case cboPusherChannelTypes.ItemIndex of
  0: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPublicChannel, txtPublishPUSHER.Text);
  1: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateChannel, txtPublishPUSHER.Text);
  2: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPresenceChannel, txtPublishPUSHER.Text);
  3: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscCacheChannel, txtPublishPUSHER.Text);
  4: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateCacheChannel, txtPublishPUSHER.Text);
  5: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPresenceCacheChannel, txtPublishPUSHER.Text);
  6: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateEncryptedChannel, txtPublishPUSHER.Text);
  7: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel, txtPublishPUSHER.Text);
  end;

procedure TfrmWebSocketClient.btnSubscribePUSHERClick(Sender: TObject);
  begin
  case cboPusherChannelTypes.ItemIndex of
  0: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPublicChannel);
  1: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateChannel);
  2: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPresenceChannel, '{"user_id": "1234", "user_info": {"name": "Phil Leggetter"}}');
  3: PUSHER.Subscribe(txtChannelPUSHER.Text, pscCacheChannel);
  4: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateCacheChannel);
  5: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPresenceCacheChannel, '{"user_id": "1234", "user_info": {"name": "Phil Leggetter"}}');
  6: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateEncryptedChannel);
  7: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel);
  end;

procedure TfrmWebSocketClient.btnUnSubscribePUSHERClick(Sender: TObject);
  begin
  case cboPusherChannelTypes.ItemIndex of
  0: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPublicChannel);
  1: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateChannel);
  2: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPresenceChannel);
  3: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscCacheChannel);
  4: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateCacheChannel);
  5: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPresenceCacheChannel);
  6: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateEncryptedChannel);
  7: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel);
  end;

procedure TfrmWebSocketClient.btnPUSHERGetChannelsClick(Sender: TObject);
  begin
  DoLog(PUSHER.GetChannels);
  end;

procedure TfrmWebSocketClient.btnPUSHERGetUsersClick(Sender: TObject);
  begin
  DoLog(PUSHER.GetUsers(txtPUSHERChannelREST.Text));
  end;

procedure TfrmWebSocketClient.btnPUSHERTriggerEventClick(Sender: TObject);
  begin
  DoLog(PUSHER.TriggerEvent(txtPUSHEREventREST.Text, txtPUSHERChannelREST.Text, txtPUSHERDataREST.Text));
  end;

PUSHER.Client := nil;
PUSHER.Pusher.AppId := txtAppIdPUSHER.Text;
PUSHER.Pusher.Cluster := txtClusterPUSHER.Text;
PUSHER.Pusher.Key := txtKeyPUSHER.Text; // your pusher api key
PUSHER.Pusher.Name := txtNamePUSHER.Text;
PUSHER.Pusher.Version := txtVersionPUSHER.Text;
```

