# TsgcWSPClient_Presence - Example

Full source of `FPresenceClient.pas` from the **02.WebSocket_Protocols/03.Presence_Protocol** demo, which uses `TsgcWSPClient_Presence`.

API reference: [TsgcWSPClient_Presence](../reference/api/TsgcWSPClient_Presence.md)
Source demo: `02.WebSocket_Protocols/03.Presence_Protocol` (file `FPresenceClient.pas`)

```pascal
unit FPresenceClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Math, sgcWebSocket_Classes, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocol_Presence_Client, sgcWebSocket_Protocols,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  sgcWebSocket_Protocol_Presence_Message, sgcBase_Classes, sgcTCP_Classes,
  sgcSocket_Classes, sgcWebSocket_Classes_SyncObjs;

type
  TForm16 = class(TForm)
    Label1: TLabel;
    btnConnect: TButton;
    btnDisconnect: TButton;
    txtMessage: TEdit;
    btnPublish: TButton;
    cboMembers: TComboBox;
    cboChannels: TComboBox;
    Label2: TLabel;
    Client: TsgcWebSocketClient;
    PresenceClient: TsgcWSPClient_Presence;
    btnSubscribe: TButton;
    btnUnsubscribe: TButton;
    txtHost: TEdit;
    txtPort: TEdit;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Log: TMemo;
    Label6: TLabel;
    chkBase64: TCheckBox;
    txtInviteId: TEdit;
    btnInvite: TButton;
    btnGetMembers: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnPublishClick(Sender: TObject);
    procedure btnSubscribeClick(Sender: TObject);
    procedure btnUnsubscribeClick(Sender: TObject);
    procedure btnGetMembersClick(Sender: TObject);
    procedure btnInviteClick(Sender: TObject);
    procedure cboChannelsChange(Sender: TObject);
    procedure PresenceClientChannelInvitation(Connection: TsgcWSConnection; const
        aMember: TsgcWSPresenceMember; const aChannel: TsgcWSPresenceChannel; var
        Accept: Boolean; var aErrorCode: Integer; var aErrorText: string);
    procedure PresenceClientChannelInvitationResponse(Connection: TsgcWSConnection;
        const aMember: TsgcWSPresenceMember; const aChannel: TsgcWSPresenceChannel;
        Accept: Boolean; const aError: TsgcWSPresenceError);
    procedure PresenceClientConnect(Connection: TsgcWSConnection);
    procedure PresenceClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure PresenceClientError(Connection: TsgcWSConnection; const Error:
        string);
    procedure PresenceClientErrorMemberChannel(Connection: TsgcWSConnection; const
        aError: TsgcWSPresenceError; const aChannel: TsgcWSPresenceChannel; const
        aMember: TsgcWSPresenceMember);
    procedure PresenceClientErrorPublishMsg(Connection: TsgcWSConnection; const
        aError: TsgcWSPresenceError; const aMsg: TsgcWSPresenceMsg; const aChannel:
        TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
    procedure PresenceClientGetMembers(Connection: TsgcWSConnection; const
        aMembers: TsgcWSPresenceMemberList; const aChannel: TsgcWSPresenceChannel);
    procedure PresenceClientNewChannelMember(Connection: TsgcWSConnection; const
        aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
    procedure PresenceClientNewMember(aConnection: TsgcWSConnection; const aMember:
        TsgcWSPresenceMember);
    procedure PresenceClientPublishMsg(Connection: TsgcWSConnection; const aMsg:
        TsgcWSPresenceMsg; const aChannel: TsgcWSPresenceChannel; const aMember:
        TsgcWSPresenceMember);
    procedure PresenceClientRemoveChannelMember(Connection: TsgcWSConnection; const
        aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
    procedure PresenceClientRemoveMember(aConnection: TsgcWSConnection; aMember:
        TsgcWSPresenceMember);
  private
    { Private declarations }
  public
    procedure DoLog(const aText: String);
    { Public declarations }
  end;

var
  Form16: TForm16;

implementation

{$R *.dfm}

procedure TForm16.FormCreate(Sender: TObject);
begin
  Randomize;
  cboMembers.ItemIndex := RandomRange(0, cboMembers.Items.Count - 1);
end;

procedure TForm16.btnConnectClick(Sender: TObject);
begin
  Log.Lines.clear;

  Client.Host := txtHost.Text;
  Client.Port := StrToInt(txtPort.Text);
  PresenceClient.Presence.Name := cboMembers.Text;
  PresenceClient.EncodeBase64 := chkBase64.Checked;
  Client.Active := True;
end;

procedure TForm16.btnDisconnectClick(Sender: TObject);
begin
  Client.Active := False;
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

procedure TForm16.cboChannelsChange(Sender: TObject);
begin
  btnSubscribe.Enabled := cboChannels.ItemIndex > 0;
  btnUnsubscribe.Enabled := cboChannels.ItemIndex > 0;
end;

procedure TForm16.DoLog(const aText: String);
begin
  Log.Lines.add(aText);
end;

procedure TForm16.PresenceClientChannelInvitation(Connection: TsgcWSConnection;
    const aMember: TsgcWSPresenceMember; const aChannel: TsgcWSPresenceChannel;
    var Accept: Boolean; var aErrorCode: Integer; var aErrorText: string);
begin
  DoLog('#invitation_received: [From] ' + aMember.Name + ' [Channel] ' + aChannel.Name);
  Accept := True;
end;

procedure TForm16.PresenceClientChannelInvitationResponse(Connection:
    TsgcWSConnection; const aMember: TsgcWSPresenceMember; const aChannel:
    TsgcWSPresenceChannel; Accept: Boolean; const aError: TsgcWSPresenceError);
begin
  if Accept then
    DoLog('#invitation_accepted: [To] ' + aMember.Name + ' [Channel] ' + aChannel.Name)
  else
    DoLog('#invitation_cancelled: [To] ' + aMember.Name + ' [Channel] ' + aChannel.Name + ' [Error] ' + aError.Text);
end;

procedure TForm16.PresenceClientConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');

  btnConnect.Enabled := False;
  btnDisconnect.Enabled := True;
end;

procedure TForm16.PresenceClientDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  DoLog('#disconnected');

  btnConnect.Enabled := True;
  btnDisconnect.Enabled := False;
end;

procedure TForm16.PresenceClientError(Connection: TsgcWSConnection; const
    Error: string);
begin
  DoLog('#error: ' + Error);
end;

procedure TForm16.PresenceClientErrorMemberChannel(Connection:
    TsgcWSConnection; const aError: TsgcWSPresenceError; const aChannel:
    TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
begin
  DoLog('#error: ' + aError.Text);
end;

procedure TForm16.PresenceClientErrorPublishMsg(Connection: TsgcWSConnection;
    const aError: TsgcWSPresenceError; const aMsg: TsgcWSPresenceMsg; const
    aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
begin
  DoLog('#error: ' + aError.Text);
end;

procedure TForm16.PresenceClientGetMembers(Connection: TsgcWSConnection; const
    aMembers: TsgcWSPresenceMemberList; const aChannel: TsgcWSPresenceChannel);
var
  i: Integer;
  oList: TList;
  oMember: TsgcWSPresenceMember;
begin
  oList := aMembers.LockList;
  Try
    for i := 0 to oList.Count - 1 do
    begin
      oMember := TsgcWSPresenceMember(oList[i]);
      DoLog('#Member: ' + oMember.Name + ' [' + oMember.ID + ']');
    end;
  Finally
    aMembers.UnlockList;
  End;
end;

procedure TForm16.PresenceClientNewChannelMember(Connection: TsgcWSConnection;
    const aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember);
begin
  DoLog('#Member: ' + aMember.Name + ' has joined channel: ' + aChannel.Name);
end;

procedure TForm16.PresenceClientNewMember(aConnection: TsgcWSConnection; const
    aMember: TsgcWSPresenceMember);
begin
  DoLog('#Member has joined: ' + aMember.Name);
end;

procedure TForm16.PresenceClientPublishMsg(Connection: TsgcWSConnection; const
    aMsg: TsgcWSPresenceMsg; const aChannel: TsgcWSPresenceChannel; const
    aMember: TsgcWSPresenceMember);
begin
  DoLog('#Message From Server: ' + aMsg.Text);
end;

procedure TForm16.PresenceClientRemoveChannelMember(Connection:
    TsgcWSConnection; const aChannel: TsgcWSPresenceChannel; const aMember:
    TsgcWSPresenceMember);
begin
  DoLog('#Member: ' + aMember.Name + ' has exit channel: ' + aChannel.Name);
end;

procedure TForm16.PresenceClientRemoveMember(aConnection: TsgcWSConnection;
    aMember: TsgcWSPresenceMember);
begin
  DoLog('#Member has exit: ' + aMember.Name);
end;

end.
```

