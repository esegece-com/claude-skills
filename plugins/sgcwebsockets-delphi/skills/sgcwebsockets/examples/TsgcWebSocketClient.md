# TsgcWebSocketClient - Example

Full source of `uClientChat.pas` from the **01.WebSocket_Quick_Start/01.Server_and_Client_Chat** demo, which uses `TsgcWebSocketClient`.

API reference: [TsgcWebSocketClient](../reference/api/TsgcWebSocketClient.md)
Source demo: `01.WebSocket_Quick_Start/01.Server_and_Client_Chat` (file `uClientChat.pas`)

```pascal
unit uClientChat;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  ExtCtrls, sgcWebSocket_Types, sgcBase_Classes, sgcTCP_Classes,
  sgcWebSocket_Classes_Indy, sgcSocket_Classes;

type
  TfrmClientChat = class(TForm)
    pnlServer: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    txtName: TEdit;
    txtMessage: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    btnSend: TButton;
    pnlServerActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlServerOptions: TPanel;
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
    chkAuthentication: TCheckBox;
    txtAuthPassword: TEdit;
    txtAuthUser: TEdit;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    procedure btnSendClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmClientChat: TfrmClientChat;

implementation

{$R *.dfm}

procedure TfrmClientChat.btnSendClick(Sender: TObject);
begin
  if WSClient.Active then
  begin
    if txtName.Text = '' then
      raise Exception.Create('Type a Name before send a message');

    if txtMessage.Text = '' then
      raise Exception.Create('Type a Message before send a message');

    WSClient.WriteData(txtName.Text + ': ' + txtMessage.Text);

    txtMessage.Text := '';
  end
  else
    raise Exception.Create('Not connected');
end;

procedure TfrmClientChat.btnStartClick(Sender: TObject);
begin
  WSClient.Authentication.Enabled := chkAuthentication.Checked;
  if WSClient.Authentication.Enabled then
  begin
    WSClient.Authentication.User := txtAuthUser.Text;
    WSClient.Authentication.Password := txtAuthPassword.Text;
  end;

  if chkTLS.Checked then
    WSClient.Port := StrToInt(txtSSLPort.Text)
  else
    WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;

  case cboOpenSSLAPI.ItemIndex of
    0:
      begin
        WSClient.TLSOptions.IOHandler := iohOpenSSL;
        WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_1_0;
      end;
    1:
      begin
        WSClient.TLSOptions.IOHandler := iohOpenSSL;
        WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
      end;
    2:
      begin
        WSClient.TLSOptions.IOHandler := iohOpenSSL;
        WSClient.TLSOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
      end;
    3:
      WSClient.TLSOptions.IOHandler := iohSChannel
  end;
  case cboTLSVersion.ItemIndex of
    0:
      WSClient.TLSOptions.Version := tlsUndefined;
    1:
      WSClient.TLSOptions.Version := tls1_0;
    2:
      WSClient.TLSOptions.Version := tls1_1;
    3:
      WSClient.TLSOptions.Version := tls1_2;
    4:
      WSClient.TLSOptions.Version := tls1_3;
  end;
  WSClient.TLS := chkTLS.Checked;

  WSClient.Proxy.Enabled := chkProxy.Checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  WSClient.Extensions.PerMessage_Deflate.Enabled := chkCompressed.Checked;

  // ... active
  WSClient.Active := True;
  if WSClient.Active then
    pnlServerOptions.Enabled := False;
end;

procedure TfrmClientChat.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlServerOptions.Enabled := True;
end;

procedure TfrmClientChat.WSClientConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('#connected');
  chkTLS.Enabled := False;
  chkCompressed.Enabled := False;
end;

procedure TfrmClientChat.WSClientDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  memoLog.Lines.Add('#disconnected (' + IntToStr(Code) + ')');
  chkTLS.Enabled := True;
  chkCompressed.Enabled := True;
end;

procedure TfrmClientChat.WSClientError(Connection: TsgcWSConnection;
  const Error: string);
begin
  memoLog.Lines.Add('#error: ' + Error);
end;

procedure TfrmClientChat.WSClientException(Connection: TsgcWSConnection;
  E: Exception);
begin
  memoLog.Lines.Add('#exception:' + E.Message);
end;

procedure TfrmClientChat.WSClientMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  memoLog.Lines.Add(Text);
end;

end.
```

