# TsgcWSPClient_AMQP1 - Example

Usage of `TsgcWSPClient_AMQP1` extracted from the **02.WebSocket_Protocols/11.AMQP1_Client** demo. See the full project for context.

API reference: [TsgcWSPClient_AMQP1](../reference/api/TsgcWSPClient_AMQP1.md)
Source demo: `02.WebSocket_Protocols/11.AMQP1_Client` (file `uClientAMQP1.pas`)

```pascal
procedure TfrmClientAMQP1.AMQP1AMQPSessionClose(Sender: TObject;
  const aSession: TsgcAMQP1Session; const aEnd: TsgcAMQP1FrameEnd);
  var
  vSession: string;
  begin
  vSession := aSession.ID;
  DoLog('#session-close: ' + aSession.ID + ' [' + IntToStr(aSession.Channel) +
  ']' + ' reason: ' + aEnd.Error.Condition);
  
  TThread.Queue(nil,
  procedure
  var
  i: Integer;
  begin
  if Assigned(listSessions) then
  begin
  for i := 0 to listSessions.GetCount - 1 do
  begin
  if listSessions.Items[i].Caption = vSession then
  listSessions.Items[i].Selected := True;
  end;
  
  listSessions.DeleteSelected;
  DoListSenderLinksDelete(vSession);
  DoListReceiverLinksDelete(vSession);
  DoListSenderLinks('');
  DoListReceiverLinks('');
  end;
  end);
  end;
  
  procedure TfrmClientAMQP1.AMQP1AMQPSessionOpen(Sender: TObject;
  const aSession: TsgcAMQP1Session; const aBegin: TsgcAMQP1FrameBegin);
  begin
  TThread.Queue(nil,
  procedure
  begin
  Sessions.Add(aSession.ID + Sessions.NameValueSeparator +
  IntToStr(aSession.Channel));
  listSessions.AddItem(aSession.ID, nil);
  DoListSenderLinks(aSession.ID);
  DoListReceiverLinks(aSession.ID);
  end);
  
  DoLog('#session-open: ' + aSession.ID + ' [' +
  IntToStr(aSession.Channel) + ']');
  end;
  
  procedure TfrmClientAMQP1.btnAzureJWTClick(Sender: TObject);
  begin
  if AMQP1.CreateAzureCbsJWT(txtAzureJWTName.Text, txtAzureJWTNamespace.Text,
  txtAzureJWTEntityName.Text, txtAzureJWTTenant.Text,
  txtAzureJWTApplicationId.Text, txtAzureJWTApplicationSecret.Text,
  StrToInt(txtAzureJWTListeningPort.Text), 3600, 10000, True) then
  ShowMessage('Azure CBS Link created!!!')
  else
  ShowMessage('The CBS Link can not be created!!!');
  end;
  
  procedure TfrmClientAMQP1.btnAzureSasTokenClick(Sender: TObject);
```

