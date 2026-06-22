# TsgcRTCPeerConnection - Example

Usage of `TsgcRTCPeerConnection` extracted from the **35.P2P/05.RTCPeerConnection** demo. See the full project for context.

API reference: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md)
Source demo: `35.P2P/05.RTCPeerConnection` (file `fRTCPeerConnection.pas`)

```pascal
procedure TFRMICE_Client.btnGatherCandidatesClick(Sender: TObject);
  begin
  btnSend.Enabled := False;
  
  sgcRTCPeerConnection.RTCOptions.WebSocket.Host := txtWebSocketHost.Text;
  sgcRTCPeerConnection.RTCOptions.WebSocket.Port := StrToInt(txtWebSocketPort.Text);
  sgcRTCPeerConnection.RTCOptions.WebSocket.Channel := txtWebSocketChannel.Text;
  sgcRTCPeerConnection.RTCOptions.WebSocket.TLS := chkWebSocketSSL.Checked;
  
  sgcRTCPeerConnection.RTCOptions.ICE.Host := txtICEHost.Text;
  sgcRTCPeerConnection.RTCOptions.ICE.Port := StrToInt(txtICEPort.Text);
  sgcRTCPeerConnection.RTCOptions.ICE.Username := txtICEUsername.Text;
  sgcRTCPeerConnection.RTCOptions.ICE.Password := txtICEPassword.Text;
  
  sgcRTCPeerConnection.RTCOptions.DTLS := chkDTLS.Checked;
  sgcRTCPeerConnection.RTCOptions.DTLSOptions.CertFile := txtCertFile.text;
  sgcRTCPeerConnection.RTCOptions.DTLSOptions.KeyFile := txtKeyFile.text;
  
  sgcRTCPeerConnection.GatherCandidates;
  end;

procedure TFRMICE_Client.btnSendClick(Sender: TObject);
  begin
  if txtMessage.Text <> '' then
  begin
  sgcRTCPeerConnection.WriteData(txtMessage.Text);
  txtMessage.Text := '';
  end
  else
  raise Exception.Create('Message is empty!');
  end;

```

