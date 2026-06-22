# TsgcWSPClient_WAMP - Example

Full source of `uClientWAMP.pas` from the **02.WebSocket_Protocols/04.WAMP_Protocol** demo, which uses `TsgcWSPClient_WAMP`.

API reference: [TsgcWSPClient_WAMP](../reference/api/TsgcWSPClient_WAMP.md)
Source demo: `02.WebSocket_Protocols/04.WAMP_Protocol` (file `uClientWAMP.pas`)

```pascal
unit uClientWAMP;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  ExtCtrls, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocol_WAMP_Client, sgcWebSocket_Protocols, sgcBase_Classes,
  sgcTCP_Classes, sgcWebSocket_Classes_Indy;

type
  TfrmClientWAMP = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    btnSubscribe: TButton;
    pnlClientActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlClientOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    chkCompressed: TCheckBox;
    chkTLS: TCheckBox;
    txtHost: TEdit;
    Label5: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    Label6: TLabel;
    txtSSLPort: TEdit;
    chkProxy: TCheckBox;
    Label7: TLabel;
    txtProxyUsername: TEdit;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyPort: TEdit;
    Label10: TLabel;
    WSPWAMP: TsgcWSPClient_WAMP;
    btnUnsubscribe: TButton;
    txtTopicURI: TEdit;
    btnPrefix: TButton;
    txtKey: TEdit;
    txtValue: TEdit;
    btnCall: TButton;
    txtCallID: TEdit;
    txtProcURI: TEdit;
    txtArguments: TEdit;
    btnPublish: TButton;
    txtTopic: TEdit;
    txtEvent: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    Label11: TLabel;
    Label12: TLabel;
    btnProgressCall: TButton;
    txtProgressCallID: TEdit;
    txtProgressProcURI: TEdit;
    txtProgressArguments: TEdit;
    Label13: TLabel;
    btnCancelCall: TButton;
    procedure btnPrefixClick(Sender: TObject);
    procedure btnSubscribeClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnUnsubscribeClick(Sender: TObject);
    procedure btnCallClick(Sender: TObject);
    procedure btnCancelCallClick(Sender: TObject);
    procedure btnPublishClick(Sender: TObject);
    procedure btnProgressCallClick(Sender: TObject);
    procedure WSPWAMPCallError(Connection: TsgcWSConnection; CallId,
        ErrorURI, ErrorDesc, ErrorDetails: string);
    procedure WSPWAMPCallResult(Connection: TsgcWSConnection; CallId,
        Result: string);
    procedure WSPWAMPConnect(Connection: TsgcWSConnection);
    procedure WSPWAMPDisconnect(Connection: TsgcWSConnection; Code:
        Integer);
    procedure WSPWAMPError(Connection: TsgcWSConnection; const Error:
        string);
    procedure WSPWAMPEvent(Connection: TsgcWSConnection; TopicURI,
        Event: string);
    procedure WSPWAMPMessage(Connection: TsgcWSConnection; const Text:
        string);
    procedure WSPWAMPWelcome(Connection: TsgcWSConnection; SessionId,
        ProtocolVersion, ServerIdent: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSPWAMPCallProgressResult(Connection: TsgcWSConnection; CallId,
        Result: string);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmClientWAMP: TfrmClientWAMP;

implementation

{$R *.dfm}

procedure TfrmClientWAMP.btnPrefixClick(Sender: TObject);
begin
  WSPWAMP.Prefix(txtKey.Text, txtValue.Text);
end;

procedure TfrmClientWAMP.btnSubscribeClick(Sender: TObject);
begin
  WSPWAMP.Subscribe(txtTopicURI.text);
end;

procedure TfrmClientWAMP.btnStartClick(Sender: TObject);
begin
  if chkTLS.Checked then
    WSClient.Port := StrToInt(txtSSLPort.Text)
  else
    WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;

  WSClient.TLS := chkTLS.Checked;

  WSClient.Proxy.Enabled := chkProxy.Checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  WSClient.Extensions.DeflateFrame.Enabled := chkCompressed.Checked;

  // ... active
  WSClient.Active := True;
  if WSClient.Active then
    pnlClientOptions.Enabled := False;
end;

procedure TfrmClientWAMP.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlClientOptions.Enabled := True;
end;

procedure TfrmClientWAMP.btnUnsubscribeClick(Sender: TObject);
begin
  WSPWAMP.UnSubscribe(txtTopicURI.Text);
end;

procedure TfrmClientWAMP.btnCallClick(Sender: TObject);
begin
  WSPWAMP.Call(txtCallId.Text, txtProcURI.Text, txtArguments.Text);
end;

procedure TfrmClientWAMP.btnCancelCallClick(Sender: TObject);
begin
  WSPWAMP.CancelCall(txtProgressCallId.Text);
end;

procedure TfrmClientWAMP.btnPublishClick(Sender: TObject);
begin
  WSPWAMP.Publish(txtTopic.Text, txtEvent.Text);
end;

procedure TfrmClientWAMP.btnProgressCallClick(Sender: TObject);
begin
  WSPWAMP.Call(txtProgressCallId.Text, txtProgressProcURI.Text, txtProgressArguments.Text);
end;

procedure TfrmClientWAMP.WSPWAMPCallError(Connection:
    TsgcWSConnection; CallId, ErrorURI, ErrorDesc, ErrorDetails: string);
begin
  memoLog.Lines.Add('#Call Error: ' + CallId + ' - ' + ErrorURI + ' - ' + ErrorDesc + ' - ' + ErrorDetails);
end;

procedure TfrmClientWAMP.WSPWAMPCallResult(Connection:
    TsgcWSConnection; CallId, Result: string);
begin
  memoLog.Lines.Add('#Call Result: ' + CallId + ' - ' + Result);
end;

procedure TfrmClientWAMP.WSPWAMPConnect(Connection:
    TsgcWSConnection);
begin
  memoLog.Lines.Add('#connected');
  chkTLS.Enabled := False;
  chkCompressed.Enabled := False;
end;

procedure TfrmClientWAMP.WSPWAMPDisconnect(Connection:
    TsgcWSConnection; Code: Integer);
begin
  memoLog.Lines.Add('#disconnected (' + IntToStr(Code) + ')');
  chkTLS.Enabled := True;
  chkCompressed.Enabled := True;
end;

procedure TfrmClientWAMP.WSPWAMPError(Connection: TsgcWSConnection;
    const Error: string);
begin
  memoLog.Lines.Add('#error: ' + Error);
end;

procedure TfrmClientWAMP.WSPWAMPEvent(Connection: TsgcWSConnection;
    TopicURI, Event: string);
begin
  memoLog.Lines.Add('#Event: ' + TopicURI + ' - ' + Event);
end;

procedure TfrmClientWAMP.WSPWAMPMessage(Connection:
    TsgcWSConnection; const Text: string);
begin
  memoLog.Lines.Add(Text);
end;

procedure TfrmClientWAMP.WSPWAMPWelcome(Connection:
    TsgcWSConnection; SessionId, ProtocolVersion, ServerIdent: string);
begin
  memoLog.Lines.Add('#Welcome: ' + SessionId + ' - ' + ProtocolVersion + ' - ' + ServerIdent);
end;

procedure TfrmClientWAMP.WSClientException(Connection: TsgcWSConnection; E:
    Exception);
begin
  MemoLog.Lines.Add('#exception:' + E.Message);
end;

procedure TfrmClientWAMP.WSPWAMPCallProgressResult(Connection:
    TsgcWSConnection; CallId, Result: string);
begin
  memoLog.Lines.Add('#Call Progress Result: ' + CallId + ' - ' + Result);
end;

end.
```

