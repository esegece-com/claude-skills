# TsgcRTCPeerConnection - Example

Full source of `fRTCPeerConnection.pas` from the **35.P2P/05.RTCPeerConnection** demo, which uses `TsgcRTCPeerConnection`.

API reference: [TsgcRTCPeerConnection](../reference/api/TsgcRTCPeerConnection.md)
Source demo: `35.P2P/05.RTCPeerConnection` (file `fRTCPeerConnection.pas`)

```pascal
unit fRTCPeerConnection;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, sgcBase_Classes,
  sgcP2P, sgcWebSocket_Classes, sgcP2P_RTCPeerConnection, sgcP2P_ICE_Classes,
  sgcP2P_ICE_Client;

type
  TFRMICE_Client = class(TForm)
    pnlTop: TPanel;
    Label1: TLabel;
    btnGatherCandidates: TButton;
    memoLog: TMemo;
    txtWebSocketHost: TEdit;
    txtWebSocketPort: TEdit;
    Label2: TLabel;
    Label3: TLabel;
    txtWebSocketChannel: TEdit;
    sgcRTCPeerConnection: TsgcRTCPeerConnection;
    chkWebSocketSSL: TCheckBox;
    Label4: TLabel;
    txtICEHost: TEdit;
    txtICEPort: TEdit;
    txtICEUsername: TEdit;
    txtICEPassword: TEdit;
    Label5: TLabel;
    chkDTLS: TCheckBox;
    txtCertFile: TEdit;
    txtKeyFile: TEdit;
    Label6: TLabel;
    Label7: TLabel;
    pnlBottom: TPanel;
    txtMessage: TEdit;
    btnSend: TButton;
    procedure btnGatherCandidatesClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
    procedure sgcRTCPeerConnectionRTCCandidatePairFailed(Sender: TObject; const
        aCandidatePair: TsgcICE_CandidatePair; const aReason: string);
    procedure sgcRTCPeerConnectionRTCCandidatePairNominated(Sender: TObject; const
        aCandidatePair: TsgcICE_CandidatePair; var Accept: Boolean);
    procedure sgcRTCPeerConnectionRTCConnect(Sender: TObject; const aCandidatePair:
        TsgcICE_CandidatePair);
    procedure sgcRTCPeerConnectionRTCException(Sender: TObject; E: Exception);
    procedure sgcRTCPeerConnectionRTCLocalCandidate(Sender: TObject; const
        aCandidate: string; var Accept: Boolean);
    procedure sgcRTCPeerConnectionRTCLocalDescription(Sender: TObject; var
        LocalDescription: string);
    procedure sgcRTCPeerConnectionRTCMessage(Sender: TObject; const aBytes:
        TArray<System.Byte>);
    procedure sgcRTCPeerConnectionRTCRemoteCandidate(Sender: TObject; const
        aCandidate: string; var Accept: Boolean);
    procedure sgcRTCPeerConnectionRTCRemoteDescription(Sender: TObject; const
        aRemoteDescription: string);
    procedure sgcRTCPeerConnectionRTCWebSocketConnect(Sender: TObject; Connection:
        TsgcWSConnection);
    procedure sgcRTCPeerConnectionRTCWebSocketDisconnect(Sender: TObject; Connection:
        TsgcWSConnection; Code: Integer);
    procedure sgcRTCPeerConnectionRTCWebSocketRemoteDisconnect(Sender: TObject;
        Connection: TsgcWSConnection; var aDisconnect: Boolean);
  public
    procedure DoLog(const aText: string);
  end;

var
  FRMICE_Client: TFRMICE_Client;

implementation

{$R *.dfm}

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

procedure TFRMICE_Client.DoLog(const aText: string);
begin
  TThread.Queue(nil,
  procedure
  begin
    if Assigned(memoLog) then
      memoLog.Lines.Add(aText);
  end);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCCandidatePairFailed(Sender:
    TObject; const aCandidatePair: TsgcICE_CandidatePair; const aReason:
    string);
begin
//  DoLog('#CandidatePair Failed: ' + aReason);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCCandidatePairNominated(Sender:
    TObject; const aCandidatePair: TsgcICE_CandidatePair; var Accept: Boolean);
begin
//  DoLog('#CandidatePair Nominated: ' + aCandidatePair.Local.AsString + ' ' + aCandidatePair.Remote.AsString);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCConnect(Sender: TObject; const
    aCandidatePair: TsgcICE_CandidatePair);
begin
  btnSend.Enabled := True;

  DoLog('#RTC Connect: ' + aCandidatePair.Local.AsString + ' ' + aCandidatePair.Remote.AsString);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCException(Sender: TObject; E:
    Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCLocalCandidate(Sender: TObject;
    const aCandidate: string; var Accept: Boolean);
begin
  DoLog('#Local Candidate: ' + aCandidate);
  Accept := Pos('relay', aCandidate) > 0;
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCLocalDescription(Sender:
    TObject; var LocalDescription: string);
begin
  DoLog('#Local Description: ' + LocalDescription);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCMessage(Sender: TObject; const
    aBytes: TArray<System.Byte>);
begin
  DoLog('#RTC: ' + TEncoding.UTF8.GetString(aBytes));
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCRemoteCandidate(Sender:
    TObject; const aCandidate: string; var Accept: Boolean);
begin
  DoLog('#Remote Candidate: ' + aCandidate);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCRemoteDescription(Sender:
    TObject; const aRemoteDescription: string);
begin
  DoLog('#Remote Description: ' + aRemoteDescription);
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCWebSocketConnect(Sender: TObject;
    Connection: TsgcWSConnection);
begin
  DoLog('#WebSocket Connected');
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCWebSocketDisconnect(Sender:
    TObject; Connection: TsgcWSConnection; Code: Integer);
begin
  DoLog('#WebSocket Disconnected');
end;

procedure TFRMICE_Client.sgcRTCPeerConnectionRTCWebSocketRemoteDisconnect(
    Sender: TObject; Connection: TsgcWSConnection; var aDisconnect: Boolean);
begin
  DoLog('#Remote Peer Disconnected');
end;

end.
```

