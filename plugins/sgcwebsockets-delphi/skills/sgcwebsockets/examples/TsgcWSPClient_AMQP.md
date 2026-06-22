# TsgcWSPClient_AMQP - Example

Usage of `TsgcWSPClient_AMQP` extracted from the **02.WebSocket_Protocols/10.AMQP_Client** demo. See the full project for context.

API reference: [TsgcWSPClient_AMQP](../reference/api/TsgcWSPClient_AMQP.md)
Source demo: `02.WebSocket_Protocols/10.AMQP_Client` (file `uClientAMQP.pas`)

```pascal
procedure TfrmClientAMQP.AMQPAMQPChannelClose(Sender: TObject;
  const aChannel: string;
  const aChannelClose: TsgcAMQPFramePayload_Method_ChannelClose; aAck: Boolean);
  begin
  DoLog('#AMQP_channel_Close: ' + aChannel + ' ' + aChannelClose.ReplyText);
  
  TThread.Queue(nil,
  procedure
  var
  i: Integer;
  begin
  if Assigned(listChannels) then
  begin
  for i := 0 to listChannels.GetCount - 1 do
  begin
  if listChannels.Items[i].Caption = aChannel then
  listChannels.Items[i].Selected := True;
  end;
  
  listChannels.DeleteSelected;
  end;
  end);
  end;
  
  procedure TfrmClientAMQP.AMQPAMQPChannelOpen(Sender: TObject;
  const aChannel: string);
  begin
  DoLog('#AMQP_channel_open: ' + aChannel);
  
  TThread.Queue(nil,
  procedure
  begin
  if Assigned(listChannels) then
  listChannels.AddItem(aChannel, nil);
  end);
  end;
  
  procedure TfrmClientAMQP.AMQPAMQPConnect(Sender: TObject);
  begin
  DoLog('#AMQP_connected');
  end;
  
  procedure TfrmClientAMQP.AMQPAMQPDisconnect(Sender: TObject;
  const aClose: TsgcAMQPFramePayload_Method_ConnectionClose; aAck: Boolean);
  begin
  DoLog('#AMQP_disconnected: ' + IntToStr(aClose.ReplyCode) + ' ' +
  aClose.ReplyText);
  
  TThread.Queue(nil,
  procedure
  begin
  if Assigned(listChannels) then
  listChannels.Clear;
  if Assigned(listExchanges) then
  listExchanges.Clear;
  end);
  end;
  
  procedure TfrmClientAMQP.AMQPAMQPException(Sender: TObject; E: Exception);
  begin
```

