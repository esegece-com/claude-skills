# TsgcICEClient - Example

Usage of `TsgcICEClient` extracted from the **35.P2P/04.ICE** demo. See the full project for context.

API reference: [TsgcICEClient](../reference/api/TsgcICEClient.md)
Source demo: `35.P2P/04.ICE` (file `fICE_Client.pas`)

```pascal
procedure TFRMICE_Client.btnGatherCandidatesClick(Sender: TObject);
  begin
  // identify the ice_client on websocket connection
  ws_client.Host := txtHost.Text;
  ws_client.Port := StrToInt(txtPort.Text);
  if cboICEClient.ItemIndex = 1 then
  ws_client.Options.Parameters := '/callee'
  else
  ws_client.Options.Parameters := '/caller';
  
  // if client connects, gather candidates
  if ws_client.Connect() then
  begin
  ice_client.GatherCandidates;
  end
  else
  raise Exception.Create('Can not connect to websocket server!!!');
  end;

procedure TFRMICE_Client.ws_clientConnect(Connection: TsgcWSConnection);
  var
  oSDP: TsgcSDP_Base;
  begin
  oSDP := TsgcSDP_Base.Create(nil);
  Try
  // set local description
  if cboICEClient.ItemIndex = 0 then
  ice_client.SetLocalDescription(sdptOffer, oSDP.AsString)
  else
  ice_client.SetLocalDescription(sdptAnswer, oSDP.AsString);
  
  // send local description
  ws_client.WriteData(oSDP.AsString);
  Finally
  FreeAndNil(oSDP);
  End;

procedure TFRMICE_Client.ws_clientMessage(Connection: TsgcWSConnection; const
  Text: string);
  begin
  // set remote description
  if LeftStr(Text, 1) = 'v' then
  begin
  if cboICEClient.ItemIndex = 1 then
  ice_client.SetRemoteDescription(sdptAnswer, Text)
  else
  ice_client.SetRemoteDescription(sdptOffer, Text);
  DoLog('[#sdp] ' + Text);
  end
  // remote candidate
  else
  begin
  ice_client.AddRTCIceCandidate(Text);
  ice_client.ProcessCandidates;
  DoLog('[#RemoteCandidate] ' + Text);
  end;
  end;

```

