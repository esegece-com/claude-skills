# TsgcICEClient - Example

Full source of `fICE_Client.pas` from the **35.P2P/04.ICE** demo, which uses `TsgcICEClient`.

API reference: [TsgcICEClient](../reference/api/TsgcICEClient.md)
Source demo: `35.P2P/04.ICE` (file `fICE_Client.pas`)

```pascal
unit fICE_Client;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, sgcSocket_Classes, sgcTCP_Classes, StrUtils,
  sgcWebSocket_Classes, sgcWebSocket_Classes_Indy, sgcWebSocket_Client,
  sgcWebSocket, sgcP2P_STUN_Classes, sgcP2P_STUN_Client, sgcP2P_TURN_Client,
  sgcP2P, sgcBase_Classes, sgcP2P_ICE_Classes, sgcP2P_ICE_Client,
  sgcP2P_ICE_Types, sgcP2P_SDP;

type
  TFRMICE_Client = class(TForm)
    pnlTop: TPanel;
    cboICEClient: TComboBox;
    Label1: TLabel;
    btnGatherCandidates: TButton;
    memoLog: TMemo;
    ice_client: TsgcICEClient;
    turn_client: TsgcTURNClient;
    ws_client: TsgcWebSocketClient;
    txtHost: TEdit;
    txtPort: TEdit;
    Label2: TLabel;
    procedure btnGatherCandidatesClick(Sender: TObject);
    procedure ice_clientICECandidate(Sender: TObject; const aCandidate:
        TsgcICE_Candidate);
    procedure ice_clientICECandidateError(Sender: TObject; const aError:
        TsgcICE_Candidate_Error);
    procedure ice_clientICECandidatePairFailed(Sender: TObject; const
        aCandidatePair: TsgcICE_CandidatePair; const aReason: string);
    procedure ice_clientICECandidatePairNominated(Sender: TObject; const
        aCandidatePair: TsgcICE_CandidatePair);
    procedure ice_clientICEException(Sender: TObject; E: Exception);
    procedure ice_clientICEReceiveBindingRequest(Sender: TObject; const aBinding:
        TsgcICE_Binding; const aMessage: TsgcSTUN_Message; var Accept: Boolean);
    procedure ws_clientConnect(Connection: TsgcWSConnection);
    procedure ws_clientMessage(Connection: TsgcWSConnection; const Text: string);
  private
  public
    procedure DoLog(const aText: string);
  end;

var
  FRMICE_Client: TFRMICE_Client;

implementation

{$R *.dfm}

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

procedure TFRMICE_Client.DoLog(const aText: string);
begin
  if Assigned(memoLog) then
    memoLog.Lines.Add(aText);
end;

procedure TFRMICE_Client.ice_clientICECandidate(Sender: TObject; const
    aCandidate: TsgcICE_Candidate);
begin
  DoLog('[#Candidate] ' + aCandidate.AsString);
  ws_client.WriteData(aCandidate.AsString);
end;

procedure TFRMICE_Client.ice_clientICECandidateError(Sender: TObject; const
    aError: TsgcICE_Candidate_Error);
begin
  DoLog(aError.Reason);
end;

procedure TFRMICE_Client.ice_clientICECandidatePairFailed(Sender: TObject;
    const aCandidatePair: TsgcICE_CandidatePair; const aReason: string);
begin
  DoLog('[#Failed] [Local]: ' + aReason + ' ' + aCandidatePair.Local.Address + ':' +
    IntToStr(aCandidatePair.Local.Port) + ' [Remote]: ' +
    aCandidatePair.Remote.Address + ':' + IntToStr(aCandidatePair.Remote.Port));
end;

procedure TFRMICE_Client.ice_clientICECandidatePairNominated(Sender: TObject;
    const aCandidatePair: TsgcICE_CandidatePair);
begin
  DoLog('[#Nominated] [Local]: ' + aCandidatePair.Local.Address + ':' +
    IntToStr(aCandidatePair.Local.Port) + ' [Remote]: ' +
    aCandidatePair.Remote.Address + ':' + IntToStr(aCandidatePair.Remote.Port));
end;

procedure TFRMICE_Client.ice_clientICEException(Sender: TObject; E: Exception);
begin
  DoLog(E.Message);
end;

procedure TFRMICE_Client.ice_clientICEReceiveBindingRequest(Sender: TObject;
    const aBinding: TsgcICE_Binding; const aMessage: TsgcSTUN_Message; var
    Accept: Boolean);
begin
  DoLog('[#ICEBinding] ' + aBinding.Username + ' ' + BoolToStr(aBinding.UseCandidate));
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

end;

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

end.
```

