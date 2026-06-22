# TsgcWSPClient_E2EE - Example

Full source of `uClientE2EE.pas` from the **02.WebSocket_Protocols/12.E2EE** demo, which uses `TsgcWSPClient_E2EE`.

API reference: [TsgcWSPClient_E2EE](../reference/api/TsgcWSPClient_E2EE.md)
Source demo: `02.WebSocket_Protocols/12.E2EE` (file `uClientE2EE.pas`)

```pascal
unit uClientE2EE;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  ExtCtrls, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Types, sgcBase_Classes, sgcSocket_Classes, sgcTCP_Classes,
  sgcWebSocket_Protocol_Base_Client, sgcWebSocket_Protocol_E2EE_Client,
  sgcWebSocket_Protocols;

type
  TfrmClientE2EE = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    pnlClientActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlClientOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    chkTLS: TCheckBox;
    txtHost: TEdit;
    Label5: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    chkProxy: TCheckBox;
    Label7: TLabel;
    txtProxyUsername: TEdit;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyPort: TEdit;
    Label10: TLabel;
    E2EE: TsgcWSPClient_E2EE;
    btnSendDirectMessage: TButton;
    txtDirectMessage: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    txtUserId: TEdit;
    Label6: TLabel;
    cboMessageTo: TComboBox;
    btnCreateGroup: TButton;
    txtGroupName: TEdit;
    Label11: TLabel;
    btnDeleteGroup: TButton;
    btnJoinGroup: TButton;
    btnLeaveGroup: TButton;
    txtGroupMessage: TEdit;
    btnSendGroupMessage: TButton;
    Label12: TLabel;
    cboGroupMembers: TComboBox;
    Label13: TLabel;
    procedure btnCreateGroupClick(Sender: TObject);
    procedure btnDeleteGroupClick(Sender: TObject);
    procedure btnJoinGroupClick(Sender: TObject);
    procedure btnLeaveGroupClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnSendDirectMessageClick(Sender: TObject);
    procedure btnSendGroupMessageClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure E2EEConnect(Connection: TsgcWSConnection);
    procedure E2EEDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure E2EEE2EEError(Sender: TObject; const aErrorCode, aErrorDescription,
        aMessage: string);
    procedure E2EEE2EEGroupCreated(Sender: TObject; const aGroup: string);
    procedure E2EEE2EEGroupDeleted(Sender: TObject; const aGroup: string);
    procedure E2EEE2EEGroupJoin(Sender: TObject; const aGroup, aMembers: string);
    procedure E2EEE2EEGroupLeave(Sender: TObject; const aGroup: string);
    procedure E2EEE2EEGroupMemberJoin(Sender: TObject; const aGroup, aUserId:
        string);
    procedure E2EEE2EEGroupMemberLeave(Sender: TObject; const aGroup, aUserId:
        string);
    procedure E2EEE2EEGroupMessageText(Sender: TObject; const aGroup, aFrom, aText:
        string);
    procedure E2EEE2EEMessageAck(Sender: TObject; const aId, aFrom, aTo, aState:
        string);
    procedure E2EEE2EEMessageText(Sender: TObject; const aFrom, aText: string);
    procedure E2EEE2EEUserCreated(Sender: TObject; const aUserId: string);
    procedure E2EEE2EEUserDeleted(Sender: TObject; const aUserId: string);
    procedure txtGroupNameChange(Sender: TObject);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
  private
    { Private declarations }
  public
    procedure DoLog(const aText: string);
    function GetRandomUserId: string;
    { Public declarations }
  end;

var
  frmClientE2EE: TfrmClientE2EE;

implementation

{$R *.dfm}

uses
  sgcE2EE_Const, sgcJSON;


procedure TfrmClientE2EE.btnCreateGroupClick(Sender: TObject);
begin
  E2EE.CreateGroup(txtGroupName.Text);
end;

procedure TfrmClientE2EE.btnDeleteGroupClick(Sender: TObject);
begin
  E2EE.DeleteGroup(txtGroupName.Text);
end;

procedure TfrmClientE2EE.btnJoinGroupClick(Sender: TObject);
begin
  E2EE.JoinGroup(txtGroupName.Text);
end;

procedure TfrmClientE2EE.btnLeaveGroupClick(Sender: TObject);
begin
  E2EE.LeaveGroup(txtGroupName.Text);
end;

procedure TfrmClientE2EE.FormCreate(Sender: TObject);
begin
  Randomize;
  txtUserId.Text := GetRandomUserId;
  E2EE.E2EE_Options.UserId := txtUserId.Text;
end;

procedure TfrmClientE2EE.btnSendDirectMessageClick(Sender: TObject);
begin
  if cboMessageTo.Text <> '' then
  begin
    E2EE.SendDirectMessage(cboMessageTo.Text, txtDirectMessage.Text);
    txtDirectMessage.Text := '';
  end;
end;

procedure TfrmClientE2EE.btnSendGroupMessageClick(Sender: TObject);
begin
  E2EE.SendGroupMessage(txtGroupName.Text, txtGroupMessage.Text);
end;

procedure TfrmClientE2EE.btnStartClick(Sender: TObject);
begin
  WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;

  WSClient.TLS := chkTLS.Checked;

  WSClient.Proxy.Enabled := chkProxy.Checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  // ... active
  WSClient.Active := True;
  if WSClient.Active then
    pnlClientOptions.Enabled := False;
end;

procedure TfrmClientE2EE.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;
  pnlClientOptions.Enabled := True;
end;

procedure TfrmClientE2EE.DoLog(const aText: string);
begin
  MemoLog.Lines.Add(aText);
end;

procedure TfrmClientE2EE.E2EEConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TfrmClientE2EE.E2EEDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmClientE2EE.E2EEE2EEError(Sender: TObject; const aErrorCode,
    aErrorDescription, aMessage: string);
begin
  DoLog('#error: ' + aErrorCode + ' ' + aErrorDescription)
end;

procedure TfrmClientE2EE.E2EEE2EEGroupCreated(Sender: TObject; const aGroup:
    string);
begin
  DoLog('#group_created: ' + aGroup);
end;

procedure TfrmClientE2EE.E2EEE2EEGroupDeleted(Sender: TObject; const aGroup:
    string);
begin
  DoLog('#group_deleted: ' + aGroup);
end;

procedure TfrmClientE2EE.E2EEE2EEGroupJoin(Sender: TObject; const aGroup,
    aMembers: string);
var
  i: Integer;
  oJSON: TsgcJSON;
  vUserId: string;
begin
  DoLog('#group_join: ' + aGroup);
  cboGroupMembers.Clear;
  oJSON := TsgcJSON.Create(nil);
  Try
    oJSON.Read(aMembers);
    for i := 0 to oJSON.Count - 1 do
    begin
      vUserId := oJSON.Item[i].Node[CS_E2EE_USER_ID].Value;
      if vUserId <> txtUserId.Text then
        cboGroupMembers.AddItem(vUserId, nil);
    end;
  Finally
    oJSON.Free;
  End;
end;

procedure TfrmClientE2EE.E2EEE2EEGroupLeave(Sender: TObject; const aGroup:
    string);
begin
  DoLog('#group_leave: ' + aGroup);
  cboGroupMembers.Clear;
end;

procedure TfrmClientE2EE.E2EEE2EEGroupMemberJoin(Sender: TObject; const aGroup,
    aUserId: string);
begin
  DoLog('#group_member_join: ' + aGroup + ' ' + aUserId);
  cboGroupMembers.AddItem(aUserId, nil);
end;

procedure TfrmClientE2EE.E2EEE2EEGroupMemberLeave(Sender: TObject; const
    aGroup, aUserId: string);
var
  i: Integer;
begin
  for i := 0 to cboGroupMembers.Items.Count - 1 do
  begin
    if cboGroupMembers.Items[i] = aUserId then
    begin
      cboGroupMembers.Items.Delete(i);
      DoLog('#group_member_leave: ' + aGroup + ' ' + aUserId);
      break;
    end;
  end;
end;

procedure TfrmClientE2EE.E2EEE2EEGroupMessageText(Sender: TObject; const
    aGroup, aFrom, aText: string);
begin
  DoLog('#group: ' + aGroup + '. aFrom: ' + aFrom + '. Text: ' + aText);
end;

procedure TfrmClientE2EE.E2EEE2EEMessageAck(Sender: TObject; const aId, aFrom,
    aTo, aState: string);
begin
  DoLog('#ack: ' + aState + ' From: ' + aFrom + ' To: ' + aTo );
end;

procedure TfrmClientE2EE.E2EEE2EEMessageText(Sender: TObject; const aFrom,
    aText: string);
begin
  DoLog('#direct_message: ' + aText);
end;

procedure TfrmClientE2EE.E2EEE2EEUserCreated(Sender: TObject; const aUserId:
    string);
begin
  cboMessageTo.AddItem(aUserId, nil);
end;

procedure TfrmClientE2EE.E2EEE2EEUserDeleted(Sender: TObject; const aUserId:
    string);
var
  i: Integer;
begin
  for i := 0 to cboMessageTo.Items.Count - 1 do
  begin
    if cboMessageTo.Items[i] = aUserId then
    begin
      cboMessageTo.Items.Delete(i);
      break;
    end;
  end;
end;

function TfrmClientE2EE.GetRandomUserId: string;
const
  Letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
var
  I: Integer;
begin
  SetLength(Result, 6);

  for I := 1 to 6 do
    Result[I] := Letters[Random(Length(Letters)) + 1];
end;

procedure TfrmClientE2EE.txtGroupNameChange(Sender: TObject);
begin
  cboGroupMembers.Clear;
end;

procedure TfrmClientE2EE.WSClientException(Connection: TsgcWSConnection; E:
    Exception);
begin
  MemoLog.Lines.Add('#exception:' + E.Message);
end;

end.
```

