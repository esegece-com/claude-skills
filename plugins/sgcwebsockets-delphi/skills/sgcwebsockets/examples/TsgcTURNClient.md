# TsgcTURNClient - Example

Full source of `FTURNClient.pas` from the **35.P2P/03.TURN** demo, which uses `TsgcTURNClient`.

API reference: [TsgcTURNClient](../reference/api/TsgcTURNClient.md)
Source demo: `35.P2P/03.TURN` (file `FTURNClient.pas`)

```pascal
unit FTURNClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcP2P, sgcP2P_STUN_Types,
  sgcP2P_STUN_Classes, sgcP2P_STUN_Client, sgcP2P_TURN_Client,
  sgcP2P_TURN_Classes, sgcSocket_Classes;

type
  TFRMSTUNClient = class(TForm)
    pnlServerOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    memoLog: TMemo;
    chkRetransmissions: TCheckBox;
    Label2: TLabel;
    txtRTO: TEdit;
    txtMaxRetries: TEdit;
    Label6: TLabel;
    Label7: TLabel;
    Label8: TLabel;
    chkLongTermCredentials: TCheckBox;
    txtUsername: TEdit;
    Label9: TLabel;
    txtPassword: TEdit;
    Label10: TLabel;
    pnlBottom: TPanel;
    btnSTUNRequestBinding: TButton;
    turn_client: TsgcTURNClient;
    pnlSTUNRequests: TPanel;
    pnlTURNRequests: TPanel;
    Label1: TLabel;
    Label11: TLabel;
    btnTURNAllocate: TButton;
    btnTURNRefresh: TButton;
    txtTURNRefreshLifetime: TEdit;
    Label12: TLabel;
    btnTURNCreatePermission: TButton;
    txtTURNCreatePermissionPeer: TEdit;
    Label13: TLabel;
    btnTURNSendIndication: TButton;
    Label14: TLabel;
    txtTURNSendIndicationPeerAddress: TEdit;
    Label15: TLabel;
    txtTURNSendIndicationPeerPort: TEdit;
    txtTURNSendIndicationData: TEdit;
    Label16: TLabel;
    btnTURNChannelBind: TButton;
    Label17: TLabel;
    txtTURNChannelBindPeerAddress: TEdit;
    Label18: TLabel;
    txtTURNChannelBindPeerPort: TEdit;
    btnTURNSendChannelData: TButton;
    Label19: TLabel;
    txtTURNSendChannelDataChannelId: TEdit;
    Label20: TLabel;
    txtTURNSendChannelDataChannelData: TEdit;
    procedure btnSTUNRequestBindingClick(Sender: TObject);
    procedure btnTURNAllocateClick(Sender: TObject);
    procedure btnTURNChannelBindClick(Sender: TObject);
    procedure btnTURNCreatePermissionClick(Sender: TObject);
    procedure btnTURNRefreshClick(Sender: TObject);
    procedure btnTURNSendChannelDataClick(Sender: TObject);
    procedure btnTURNSendIndicationClick(Sender: TObject);
    procedure turn_clientSTUNException(Sender: TObject; E: Exception);
    procedure turn_clientSTUNResponseError(Sender: TObject; const aSocket:
        TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aError:
        TsgcSTUN_ResponseError);
    procedure turn_clientSTUNResponseSuccess(Sender: TObject; const aSocket:
        TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aBinding:
        TsgcSTUN_ResponseBinding);
    procedure turn_clientTURNAllocate(Sender: TObject;
      const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
      const aAllocation: TsgcTURN_ResponseAllocation);
    procedure turn_clientTURNChannelBind(Sender: TObject;
      const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
      const aChannelBind: TsgcTURN_ResponseChannelBind);
    procedure turn_clientTURNChannelData(Sender: TObject;
      const aSocket: TsgcSocketConnection;
      const aChannelData: TsgcTURNChannelData);
    procedure turn_clientTURNCreatePermission(Sender: TObject;
      const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
      const aCreatePermission: TsgcTURN_ResponseCreatePermission);
    procedure turn_clientTURNDataIndication(Sender: TObject;
      const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
      const aDataIndication: TsgcTURN_ResponseDataIndication);
    procedure turn_clientTURNRefresh(Sender: TObject;
      const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
      const aRefresh: TsgcTURN_ResponseRefresh);
  private
    procedure DoInitialize;
    procedure DoLog(const aText: String);
  end;

var
  FRMSTUNClient: TFRMSTUNClient;

implementation

uses
  sgcP2P_STUN_Helpers;

{$R *.dfm}

procedure TFRMSTUNClient.btnSTUNRequestBindingClick(Sender: TObject);
begin
  DoInitialize;
  // send request binding
  turn_client.SendRequest;
end;

procedure TFRMSTUNClient.btnTURNAllocateClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.Allocate;
end;

procedure TFRMSTUNClient.btnTURNChannelBindClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.ChannelBind(txtTURNChannelBindPeerAddress.Text,
    StrToInt(txtTURNChannelBindPeerPort.Text));
end;

procedure TFRMSTUNClient.btnTURNCreatePermissionClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.CreatePermission(txtTURNCreatePermissionPeer.Text);
end;

procedure TFRMSTUNClient.btnTURNRefreshClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.Refresh(StrToInt(txtTURNRefreshLifetime.Text));
end;

procedure TFRMSTUNClient.btnTURNSendChannelDataClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.SendChannelData(StrToInt(txtTURNSendChannelDataChannelId.Text),
    txtTURNSendChannelDataChannelData.Text);
end;

procedure TFRMSTUNClient.btnTURNSendIndicationClick(Sender: TObject);
begin
  DoInitialize;
  turn_client.SendIndication(txtTURNSendIndicationPeerAddress.Text,
    StrToInt(txtTURNSendIndicationPeerPort.Text),
    txtTURNSendIndicationData.Text);
end;

procedure TFRMSTUNClient.DoInitialize;
begin
  // turn server
  turn_client.Host := txtHost.Text;
  turn_client.Port := StrToInt(txtPort.Text);
  // retransmissions
  turn_client.RetransmissionOptions.Enabled := chkRetransmissions.Checked;
  turn_client.RetransmissionOptions.RTO := StrToInt(txtRTO.Text);
  turn_client.RetransmissionOptions.MaxRetries := StrToInt(txtMaxRetries.Text);
  // stun
  turn_client.STUNOptions.Authentication.Credentials := stauNone;
  // turn
  if chkLongTermCredentials.Checked then
  begin
    turn_client.TURNOptions.Authentication.Credentials :=
      stauLongTermCredential;
    turn_client.TURNOptions.Fingerprint := True;
  end
  else
  begin
    turn_client.TURNOptions.Authentication.Credentials := stauNone;
    turn_client.TURNOptions.Fingerprint := False;
  end;
  turn_client.TURNOptions.Authentication.Username := txtUsername.Text;
  turn_client.TURNOptions.Authentication.Password := txtPassword.Text;
end;

procedure TFRMSTUNClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMSTUNClient.turn_clientSTUNException(Sender: TObject;
  E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMSTUNClient.turn_clientSTUNResponseError(Sender: TObject; const
    aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const
    aError: TsgcSTUN_ResponseError);
begin
  DoLog('#error: ' + IntToStr(aError.Code) + ' ' + aError.Reason);
end;

procedure TFRMSTUNClient.turn_clientSTUNResponseSuccess(Sender: TObject; const
    aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const
    aBinding: TsgcSTUN_ResponseBinding);
var
  i: Integer;
begin
  DoLog('#binding: ' + aBinding.RemoteIP + ':' + IntToStr(aBinding.RemotePort));

  for i := 0 to aMessage.Attributes.Count - 1 do
  begin
    case TsgcSTUN_Attribute(aMessage.Attributes.Items[i]).AttributeType of
      stmaFingerprint:
        DoLog('#fingerprint: ' + IntToStr(TsgcSTUN_Attribute_FINGERPRINT
          (aMessage.Attributes.Items[i]).Fingerprint));
      stmaSoftware:
        DoLog('#software: ' + TsgcSTUN_Attribute_SOFTWARE
          (aMessage.Attributes.Items[i]).Software);
      stmaResponse_Origin:
        DoLog('#response_origin: ' + TsgcSTUN_Attribute_RESPONSE_ORIGIN
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_RESPONSE_ORIGIN(aMessage.Attributes.Items
          [i]).Port));
      stmaOther_Address:
        DoLog('#other_address: ' + TsgcSTUN_Attribute_OTHER_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_OTHER_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
      stmaSource_Address:
        DoLog('#source_address: ' + TsgcSTUN_Attribute_SOURCE_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_SOURCE_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
      stmaChanged_Address:
        DoLog('#changed_address: ' + TsgcSTUN_Attribute_CHANGED_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_CHANGED_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
    end;
  end;
end;

procedure TFRMSTUNClient.turn_clientTURNAllocate(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
  const aAllocation: TsgcTURN_ResponseAllocation);
begin
  DoLog('#Allocate: ' + aAllocation.RelayedIP + ':' +
    IntToStr(aAllocation.RelayedPort));
end;

procedure TFRMSTUNClient.turn_clientTURNChannelBind(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
  const aChannelBind: TsgcTURN_ResponseChannelBind);
begin
  DoLog('#Channel Bind: ' + IntToStr(aChannelBind.Channel));
end;

procedure TFRMSTUNClient.turn_clientTURNChannelData(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aChannelData: TsgcTURNChannelData);
begin
  DoLog('#Channel Data: [' + IntToStr(aChannelData.ChannelID) + '] ' +
    sgcGetStringFromBytes(aChannelData.Data));
end;

procedure TFRMSTUNClient.turn_clientTURNCreatePermission(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
  const aCreatePermission: TsgcTURN_ResponseCreatePermission);
begin
  DoLog('#Create Permission: ' + aCreatePermission.IPAddresses.Text);
end;

procedure TFRMSTUNClient.turn_clientTURNDataIndication(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
  const aDataIndication: TsgcTURN_ResponseDataIndication);
begin
  DoLog('#Data Indication: [' + aDataIndication.PeerIP + ':' +
    IntToStr(aDataIndication.PeerPort) + '] ' + sgcGetStringFromBytes
    (aDataIndication.Data));
end;

procedure TFRMSTUNClient.turn_clientTURNRefresh(Sender: TObject;
  const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message;
  const aRefresh: TsgcTURN_ResponseRefresh);
begin
  DoLog('#Refresh: ' + IntToStr(aRefresh.Lifetime));
end;

end.
```

