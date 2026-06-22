# TsgcWSPClient_AMQP1 - Example

Full source of `uClientAMQP1.pas` from the **02.WebSocket_Protocols/11.AMQP1_Client** demo, which uses `TsgcWSPClient_AMQP1`.

API reference: [TsgcWSPClient_AMQP1](../reference/api/TsgcWSPClient_AMQP1.md)
Source demo: `02.WebSocket_Protocols/11.AMQP1_Client` (file `uClientAMQP1.pas`)

```pascal
unit uClientAMQP1;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ComCtrls, Menus, StdCtrls, ExtCtrls,
  sgcWebSocket_Protocol_Base_Client, sgcWebSocket_Classes, sgcWebSocket_Client,
  sgcWebSocket,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Protocol_AMQP1_Client, sgcAMQP1_Classes, sgcBase_Classes,
  sgcSocket_Classes, sgcTCP_Classes, sgcWebSocket_Classes_SyncObjs,
  sgcAMQP1_Frames, sgcAMQP1_Session, sgcAMQP1_Message;

type
  TfrmClientAMQP1 = class(TForm)
    pnlClient: TPanel;
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
    Label6: TLabel;
    txtSSLPort: TEdit;
    AMQP1: TsgcWSPClient_AMQP1;
    txtUser: TEdit;
    txtPassword: TEdit;
    Label11: TLabel;
    Label13: TLabel;
    PageControl1: TPageControl;
    tabChannelExchangesQueues: TTabSheet;
    listSessions: TListView;
    btnSessionOpen: TButton;
    txtSession: TEdit;
    popupSessions: TPopupMenu;
    SessionClose1: TMenuItem;
    listSenderLinks: TListView;
    btnNewSenderLink: TButton;
    Label14: TLabel;
    Label15: TLabel;
    popupSenderLinks: TPopupMenu;
    CloseSenderLink1: TMenuItem;
    Label16: TLabel;
    listReceiverLinks: TListView;
    txtReceiverLink: TEdit;
    popupReceiverLinks: TPopupMenu;
    CloseReceiverLink1: TMenuItem;
    txtSenderLink: TEdit;
    PageControl2: TPageControl;
    tabPublishMessages: TTabSheet;
    txtSendMessage: TEdit;
    btnSendMessage: TButton;
    btnNewReceiverLink: TButton;
    tabGetMessages: TTabSheet;
    btnGetMessage: TButton;
    cboLinkReadMode: TComboBox;
    Label1: TLabel;
    Label2: TLabel;
    Label12: TLabel;
    Label17: TLabel;
    txtSenderSource: TEdit;
    Label18: TLabel;
    txtReceiverTarget: TEdit;
    Label19: TLabel;
    cboLinkSendMode: TComboBox;
    chkWebSockets: TCheckBox;
    Label20: TLabel;
    txtParameters: TEdit;
    pnlTop: TPanel;
    PageControl3: TPageControl;
    tabProxy: TTabSheet;
    chkProxy: TCheckBox;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyUsername: TEdit;
    Label7: TLabel;
    txtProxyPort: TEdit;
    Label10: TLabel;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    tabAzureSasToken: TTabSheet;
    cboServer: TComboBox;
    Label21: TLabel;
    memoLog: TMemo;
    txtAzureSasName: TEdit;
    txtAzureSasNamespace: TEdit;
    txtAzureSasEntityName: TEdit;
    txtAzureSasKeyName: TEdit;
    txtAzureSasKeyValue: TEdit;
    txtAzureSasExpiration: TEdit;
    txtAzureSasTimeout: TEdit;
    Label22: TLabel;
    Label23: TLabel;
    Label24: TLabel;
    Label25: TLabel;
    Label26: TLabel;
    Label27: TLabel;
    Label28: TLabel;
    TabSheet1: TTabSheet;
    Label29: TLabel;
    txtAzureJWTName: TEdit;
    Label30: TLabel;
    txtAzureJWTNamespace: TEdit;
    Label31: TLabel;
    txtAzureJWTEntityName: TEdit;
    Label32: TLabel;
    txtAzureJWTTenant: TEdit;
    Label33: TLabel;
    txtAzureJWTApplicationId: TEdit;
    Label34: TLabel;
    txtAzureJWTApplicationSecret: TEdit;
    Label35: TLabel;
    txtAzureJWTListeningPort: TEdit;
    btnAzureSasToken: TButton;
    btnAzureJWT: TButton;
    procedure FormCreate(Sender: TObject);
    procedure AMQP1AMQPBeforeReadFrame(Sender: TObject;
      const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
    procedure AMQP1AMQPBeforeWriteFrame(Sender: TObject;
      const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
    procedure AMQP1AMQPClose(Sender: TObject;
      const aError: TsgcAMQP1FrameError);
    procedure AMQP1AMQPConnect(Sender: TObject;
      const aOpen: TsgcAMQP1FrameOpen);
    procedure AMQP1AMQPDisconnect(Sender: TObject; const aCode: Integer);
    procedure AMQP1AMQPException(Sender: TObject; E: Exception);
    procedure AMQP1AMQPLinkClose(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link;
      const aDetach: TsgcAMQP1FrameDetach);
    procedure AMQP1AMQPLinkOpen(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link;
      const aAttach: TsgcAMQP1FrameAttach);
    procedure AMQP1AMQPMessage(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1ReceiverLink;
      const aMessage: TsgcAMQP1Message;
      var DeliveryState: TsgcAMQP1MessageDeliveryState);
    procedure AMQP1AMQPMessageSent(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink;
      const aMessageId: string);
    procedure AMQP1AMQPMessageSentAck(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink;
      const aMessageId: string;
      const aDeliveryState: TsgcAMQP1FrameDeliveryStates;
      const aDisposition: TsgcAMQP1FrameDisposition);
    procedure AMQP1AMQPSASLAuthentication(Sender: TObject;
      aCode: TsgcAMQP1SaslCode; const aDescription: string;
      var Handled: Boolean);
    procedure AMQP1AMQPSessionClose(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aEnd: TsgcAMQP1FrameEnd);
    procedure AMQP1AMQPSessionOpen(Sender: TObject;
      const aSession: TsgcAMQP1Session; const aBegin: TsgcAMQP1FrameBegin);
    procedure btnAzureJWTClick(Sender: TObject);
    procedure btnAzureSasTokenClick(Sender: TObject);
    procedure btnGetMessageClick(Sender: TObject);
    procedure btnNewReceiverLinkClick(Sender: TObject);
    procedure btnNewSenderLinkClick(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure btnSessionOpenClick(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure cboServerChange(Sender: TObject);
    procedure CloseReceiverLink1Click(Sender: TObject);
    procedure CloseSenderLink1Click(Sender: TObject);
    procedure listSenderLinksClick(Sender: TObject);
    procedure listReceiverLinksClick(Sender: TObject);
    procedure listSessionsClick(Sender: TObject);
    procedure SessionClose1Click(Sender: TObject);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
  private
    FSessions: TStringList;
    FSenderLinks: TStringList;
    FReceiverLinks: TStringList;
    procedure DoListSenderLinks(const aSession: string);
    procedure DoListSenderLinksDelete(const aSession: string);
    procedure DoListReceiverLinks(const aSession: string);
    procedure DoListReceiverLinksDelete(const aSession: string);
    procedure DoLog(const aText: string);
    function GetSessions: TStringList;
    function GetSenderLinks: TStringList;
    function GetReceiverLinks: TStringList;
  public
    property Sessions: TStringList read GetSessions write FSessions;
    property SenderLinks: TStringList read GetSenderLinks write FSenderLinks;
    property ReceiverLinks: TStringList read GetReceiverLinks
      write FReceiverLinks;
  end;

var
  frmClientAMQP1: TfrmClientAMQP1;

implementation

uses
  sgcBase_Helpers;

{$R *.dfm}

procedure TfrmClientAMQP1.FormCreate(Sender: TObject);
var
  vAddress: string;
begin
  // ... random source/target for demo purposes
  vAddress := FormatDateTime('yyyymmsshhnnss', Now);
  txtSenderSource.Text := vAddress;
  txtReceiverTarget.Text := vAddress;
end;

procedure TfrmClientAMQP1.AMQP1AMQPBeforeReadFrame(Sender: TObject;
  const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
begin
  Handled := False;
end;

procedure TfrmClientAMQP1.AMQP1AMQPBeforeWriteFrame(Sender: TObject;
  const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
begin
  Handled := False;
end;

procedure TfrmClientAMQP1.AMQP1AMQPClose(Sender: TObject;
  const aError: TsgcAMQP1FrameError);
begin
  DoLog('#close: ' + aError.Condition + ' ' + aError.Description + ' ' +
    aError.Info);
end;

procedure TfrmClientAMQP1.AMQP1AMQPConnect(Sender: TObject;
  const aOpen: TsgcAMQP1FrameOpen);
begin
  DoLog('#connect: ' + aOpen.Properties);
end;

procedure TfrmClientAMQP1.AMQP1AMQPDisconnect(Sender: TObject;
  const aCode: Integer);
begin
  Sessions.Clear;
  ReceiverLinks.Clear;
  SenderLinks.Clear;
  listSessions.Clear;
  listReceiverLinks.Clear;
  listSenderLinks.Clear;

  DoLog('#disconnect');
end;

procedure TfrmClientAMQP1.AMQP1AMQPException(Sender: TObject; E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TfrmClientAMQP1.AMQP1AMQPLinkClose(Sender: TObject;
  const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link;
  const aDetach: TsgcAMQP1FrameDetach);
var
  vSession, vLink: string;
  vMode: TsgcAMQP1LinkMode;
begin
  vSession := aSession.ID;
  vLink := aLink.Name;
  vMode := aLink.Mode;
  DoLog('#link-close: ' + vLink);

  TThread.Queue(nil,
    procedure
    var
      i: Integer;
    begin
      case vMode of
        amqp1lnkReceiver:
          begin
            i := ReceiverLinks.IndexOf(vSession +
              ReceiverLinks.NameValueSeparator + vLink);
            if i > -1 then
            begin
              ReceiverLinks.Delete(i);
              DoListReceiverLinks(vSession);
            end;
          end;
        amqp1lnkSender:
          begin
            i := SenderLinks.IndexOf(vSession +
              SenderLinks.NameValueSeparator + vLink);
            if i > -1 then
            begin
              SenderLinks.Delete(i);
              DoListSenderLinks(vSession);
            end;
          end;
      end;
    end);
end;

procedure TfrmClientAMQP1.AMQP1AMQPLinkOpen(Sender: TObject;
const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link;
const aAttach: TsgcAMQP1FrameAttach);
begin
  DoLog('#link-open: ' + aLink.Name);

  TThread.Queue(nil,
    procedure
    begin
      case aLink.Mode of
        amqp1lnkReceiver:
          begin
            ReceiverLinks.Add(aSession.ID + ReceiverLinks.NameValueSeparator +
              aLink.ID);
            DoListReceiverLinks(aSession.ID);
          end;
        amqp1lnkSender:
          begin
            SenderLinks.Add(aSession.ID + SenderLinks.NameValueSeparator +
              aLink.ID);
            DoListSenderLinks(aSession.ID);
          end;
      end;
    end);
end;

procedure TfrmClientAMQP1.AMQP1AMQPMessage(Sender: TObject;
const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1ReceiverLink;
const aMessage: TsgcAMQP1Message;
var DeliveryState: TsgcAMQP1MessageDeliveryState);
begin
  case aMessage.ApplicationData.ValueType of
    amqp1adtData:
      DoLog(sgcBytesToStringRaw(aMessage.ApplicationData.Data.Binary));
    amqp1adtAmqpValue:
      DoLog(aMessage.ApplicationData.AMQPValue.Value);
  end;
end;

procedure TfrmClientAMQP1.AMQP1AMQPMessageSent(Sender: TObject;
const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink;
const aMessageId: string);
begin
  DoLog('#message-sent: ' + aMessageId);
end;

procedure TfrmClientAMQP1.AMQP1AMQPMessageSentAck(Sender: TObject;
const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink;
const aMessageId: string; const aDeliveryState: TsgcAMQP1FrameDeliveryStates;
const aDisposition: TsgcAMQP1FrameDisposition);

var
  vMessageId: string;
begin
  vMessageId := aMessageId;
  case aDeliveryState of
    amqp1fdtsAccepted:
      DoLog('#msg-accepted: ' + vMessageId);
    amqp1fdtsRejected:
      DoLog('#msg-rejected: ' + vMessageId + ' ' + TsgcAMQP1FrameRejected
        (aDisposition.State).Error.Condition + ' ' + TsgcAMQP1FrameRejected
        (aDisposition.State).Error.Description);
    amqp1fdtsReleased:
      DoLog('#msg-released: ' + vMessageId);
    amqp1fdtsModified:
      DoLog('#msg-modified: ' + vMessageId + ' ' + TsgcAMQP1FrameModified
        (aDisposition.State).MessageAnnotations);
    amqp1fdtsReceived:
      DoLog('#msg-received: ' + vMessageId);
  end;
end;

procedure TfrmClientAMQP1.AMQP1AMQPSASLAuthentication(Sender: TObject;
aCode: TsgcAMQP1SaslCode; const aDescription: string; var Handled: Boolean);
begin
  DoLog('#sasl-authentication: ' + aDescription);
end;

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
begin
  if AMQP1.CreateAzureCbsSasToken(txtAzureSasName.Text,
    txtAzureSasNamespace.Text, txtAzureSasEntityName.Text,
    txtAzureSasKeyName.Text, txtAzureSasKeyValue.Text,
    StrToInt(txtAzureSasExpiration.Text), StrToInt(txtAzureSasTimeout.Text),
    True) then
    ShowMessage('Azure CBS Link created!!!')
  else
    ShowMessage('The CBS Link can not be created!!!');
end;

procedure TfrmClientAMQP1.btnGetMessageClick(Sender: TObject);
begin
  AMQP1.GetMessage(txtSession.Text, txtReceiverLink.Text);
end;

procedure TfrmClientAMQP1.btnNewReceiverLinkClick(Sender: TObject);
var
  oOptions: TsgcAMQP1MethodOptions_CreateReceiverLink;
begin
  oOptions := TsgcAMQP1MethodOptions_CreateReceiverLink.Create;
  Try
    oOptions.Await := True;
    case cboLinkReadMode.ItemIndex of
      0:
        oOptions.ReadMode := amqp1srmAuto;
      1:
        oOptions.ReadMode := amqp1srmManual;
    end;
    AMQP1.CreateReceiverLink(txtSession.Text, txtReceiverLink.Text,
      txtReceiverTarget.Text, oOptions);
  Finally
    oOptions.Free;
  End;
end;

procedure TfrmClientAMQP1.btnNewSenderLinkClick(Sender: TObject);
var
  oOptions: TsgcAMQP1MethodOptions_CreateSenderLink;
begin
  oOptions := TsgcAMQP1MethodOptions_CreateSenderLink.Create;
  Try
    oOptions.Await := True;
    case cboLinkSendMode.ItemIndex of
      0:
        oOptions.SndSettleMode := amqp1ssmUnsettled;
      1:
        oOptions.SndSettleMode := amqp1ssmsettled;
    else
      oOptions.SndSettleMode := amqp1ssmMixed;
    end;
    AMQP1.CreateSenderLink(txtSession.Text, txtSenderLink.Text,
      txtSenderSource.Text, oOptions);
  Finally
    oOptions.Free;
  End;
end;

procedure TfrmClientAMQP1.btnSendMessageClick(Sender: TObject);
begin
  if (txtSession.Text <> '') and (txtSenderLink.Text <> '') then
    AMQP1.SendMessage(txtSession.Text, txtSenderLink.Text, txtSendMessage.Text,
      FormatDateTime('hhnnsszzz', Now));
end;

procedure TfrmClientAMQP1.btnSessionOpenClick(Sender: TObject);
var
  oOptions: TsgcAMQP1MethodOptions_SessionOpen;
begin
  oOptions := TsgcAMQP1MethodOptions_SessionOpen.Create;
  Try
    oOptions.Await := True;
    AMQP1.CreateSession(txtSession.Text, oOptions);
  Finally
    oOptions.Free;
  End;
end;

procedure TfrmClientAMQP1.FormDestroy(Sender: TObject);
begin
  WSClient.Active := False;
  FreeAndNil(FSessions);
  FreeAndNil(FReceiverLinks);
  FreeAndNil(FSenderLinks);
end;

procedure TfrmClientAMQP1.btnStartClick(Sender: TObject);
begin
  WSClient.NotifyEvents := neNoSync;
  WSClient.Specifications.RFC6455 := chkWebSockets.Checked;

  if txtUser.Text <> '' then
  begin
    AMQP1.AMQPOptions.Authentication.AuthType := amqp1authSASLPlain;
    AMQP1.AMQPOptions.Authentication.Username := txtUser.Text;
    AMQP1.AMQPOptions.Authentication.Password := txtPassword.Text;
  end
  else
  begin
    AMQP1.AMQPOptions.Authentication.AuthType := amqp1authSASLAnonymous;
    AMQP1.AMQPOptions.Authentication.Username := 'guest';
    AMQP1.AMQPOptions.Authentication.Password := 'guest';
  end;

  if chkTLS.Checked then
    WSClient.Port := StrToInt(txtSSLPort.Text)
  else
    WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;
  WSClient.Options.Parameters := txtParameters.Text;

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

procedure TfrmClientAMQP1.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlClientOptions.Enabled := True;
end;

procedure TfrmClientAMQP1.cboServerChange(Sender: TObject);
var
  vServiceBus: string;
begin
  case cboServer.ItemIndex of
    0:
      begin
        txtHost.Text := 'www.esegece.com';
        txtParameters.Text := '/';
        txtUser.Text := 'sgc';
        txtPassword.Text := 'sgc';
        txtDefaultPort.Text := '5672';
        txtSSLPort.Text := '5671';
        chkTLS.Checked := True;
        chkWebSockets.Checked := False;
      end;
    1:
      begin
        vServiceBus := InputBox('Azure Service Bus',
          'Set the Service Bus Namespace.', '');
        txtHost.Text := vServiceBus + '.servicebus.windows.net';
        txtParameters.Text := '/';
        txtUser.Text := '';
        txtPassword.Text := '';
        txtDefaultPort.Text := '5672';
        txtSSLPort.Text := '5671';
        chkTLS.Checked := True;
        chkWebSockets.Checked := False;
      end;
    2:
      begin
        vServiceBus := InputBox('Azure Service Bus',
          'Set the Service Bus Namespace.', '');
        txtHost.Text := vServiceBus + '.servicebus.windows.net';
        txtParameters.Text := '/$servicebus/websocket';
        txtUser.Text := '';
        txtPassword.Text := '';
        txtDefaultPort.Text := '5672';
        txtSSLPort.Text := '443';
        chkTLS.Checked := True;
        chkWebSockets.Checked := True;
      end;
  end;
end;

procedure TfrmClientAMQP1.CloseReceiverLink1Click(Sender: TObject);
begin
  if (txtSession.Text <> '') and (txtReceiverLink.Text <> '') then
    AMQP1.CloseLink(txtSession.Text, txtReceiverLink.Text);
end;

procedure TfrmClientAMQP1.CloseSenderLink1Click(Sender: TObject);
begin
  if (txtSession.Text <> '') and (txtSenderLink.Text <> '') then
    AMQP1.CloseLink(txtSession.Text, txtSenderLink.Text);
end;

procedure TfrmClientAMQP1.DoListReceiverLinks(const aSession: string);
var
  i: Integer;
begin
  listReceiverLinks.Clear;

  for i := 0 to ReceiverLinks.Count - 1 do
  begin
    if ReceiverLinks.Names[i] = aSession then
    begin
      listReceiverLinks.AddItem(ReceiverLinks.ValueFromIndex[i], nil);
    end;
  end;
end;

procedure TfrmClientAMQP1.DoListSenderLinks(const aSession: string);
var
  i: Integer;
begin
  listSenderLinks.Clear;

  for i := 0 to SenderLinks.Count - 1 do
  begin
    if SenderLinks.Names[i] = aSession then
    begin
      listSenderLinks.AddItem(SenderLinks.ValueFromIndex[i], nil);
    end;
  end;
end;

procedure TfrmClientAMQP1.DoListSenderLinksDelete(const aSession: string);
var
  i: Integer;
begin
  for i := SenderLinks.Count - 1 Downto 0 do
  begin
    if SenderLinks.Names[i] = aSession then
      SenderLinks.Delete(i);
  end;
end;

procedure TfrmClientAMQP1.DoListReceiverLinksDelete(const aSession: string);
var
  i: Integer;
begin
  for i := ReceiverLinks.Count - 1 Downto 0 do
  begin
    if ReceiverLinks.Names[i] = aSession then
      ReceiverLinks.Delete(i);
  end;
end;

procedure TfrmClientAMQP1.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add(aText);
    end);
end;

function TfrmClientAMQP1.GetSessions: TStringList;
begin
  if not Assigned(FSessions) then
    FSessions := TStringList.Create;
  Result := FSessions;
end;

function TfrmClientAMQP1.GetSenderLinks: TStringList;
begin
  if not Assigned(FSenderLinks) then
    FSenderLinks := TStringList.Create;
  Result := FSenderLinks;
end;

function TfrmClientAMQP1.GetReceiverLinks: TStringList;
begin
  if not Assigned(FReceiverLinks) then
    FReceiverLinks := TStringList.Create;
  Result := FReceiverLinks;
end;

procedure TfrmClientAMQP1.listSenderLinksClick(Sender: TObject);
var
  i: Integer;
begin
  txtSenderLink.Text := '';
  i := listSenderLinks.ItemIndex;
  if i >= 0 then
    txtSenderLink.Text := listSenderLinks.Items[i].Caption;
end;

procedure TfrmClientAMQP1.listReceiverLinksClick(Sender: TObject);
var
  i: Integer;
begin
  txtReceiverLink.Text := '';
  i := listReceiverLinks.ItemIndex;
  if i >= 0 then
    txtReceiverLink.Text := listReceiverLinks.Items[i].Caption;
end;

procedure TfrmClientAMQP1.listSessionsClick(Sender: TObject);
var
  i: Integer;
begin
  i := listSessions.ItemIndex;
  if i >= 0 then
  begin
    txtSession.Text := listSessions.Items[i].Caption;
    DoListSenderLinks(txtSession.Text);
    DoListReceiverLinks(txtSession.Text);
  end
  else
  begin
    listSenderLinks.Clear;
    listReceiverLinks.Clear;
  end;
end;

procedure TfrmClientAMQP1.SessionClose1Click(Sender: TObject);
begin
  if txtSession.Text <> '' then
    AMQP1.CloseSession(txtSession.Text);
end;

procedure TfrmClientAMQP1.WSClientException(Connection: TsgcWSConnection;
E: Exception);
begin
  DoLog('#exception:' + E.Message);
end;

end.
```

