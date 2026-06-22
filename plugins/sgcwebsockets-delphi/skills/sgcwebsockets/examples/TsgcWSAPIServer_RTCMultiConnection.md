# TsgcWSAPIServer_RTCMultiConnection - Example

Full source of `uServerRTCMultiConnection.pas` from the **30.WebRTC_Protocol/04.RTCMultiConnection** demo, which uses `TsgcWSAPIServer_RTCMultiConnection`.

API reference: [TsgcWSAPIServer_RTCMultiConnection](../reference/api/TsgcWSAPIServer_RTCMultiConnection.md)
Source demo: `30.WebRTC_Protocol/04.RTCMultiConnection` (file `uServerRTCMultiConnection.pas`)

```pascal
unit uServerRTCMultiConnection;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils,
  HTTPApp, HTTPProd,
  // indy
  IdContext, IdCustomHTTPServer,
  // sgc
  sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket,
  sgcBase_Helpers, sgcWebSocket_Classes_Indy, sgcBase_Classes, sgcTCP_Classes,
  sgcSocket_Classes, sgcWebSocket_Server_API_SocketIO,
  sgcWebSocket_Server_API_RTCMultiConnection, sgcWebSocket_Server_APIs;

type
  TfrmServerRTCMultiConnection = class(TForm)
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    btnEdge: TButton;
    pnlServerActive: TPanel;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    pnlBrowsers: TPanel;
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    pageRTCMultiConnection: TPageProducer;
    RTCMultiConnection: TsgcWSAPIServer_RTCMultiConnection;
    Panel1: TPanel;
    Label4: TLabel;
    cboPages: TComboBox;
    Label5: TLabel;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnEdgeClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure pageRTCMultiConnectionHTMLTag(Sender: TObject; Tag: TTag; const TagString: string;
        TagParams: TStrings; var ReplaceText: string);
    procedure WSPAppRTCConnect(Connection: TsgcWSConnection);
    procedure WSPAppRTCDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSPAppRTCError(Connection: TsgcWSConnection; const Error: string);
    procedure WSPAppRTCMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSPAppRTCSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPAppRTCUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
  private
    procedure DoOpenBrowser(const aBrowserName: string);
    function GetHTMLPage: string;
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmServerRTCMultiConnection: TfrmServerRTCMultiConnection;

implementation

uses
  ShellAPI;

{$R *.dfm}

procedure TfrmServerRTCMultiConnection.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServerRTCMultiConnection.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServerRTCMultiConnection.btnEdgeClick(Sender: TObject);
begin
  DoOpenBrowser('msedge');
end;

procedure TfrmServerRTCMultiConnection.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServerRTCMultiConnection.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServerRTCMultiConnection.btnStartClick(Sender: TObject);
begin
  WSServer.Port := StrToInt(txtDefaultPort.Text);

  // ... bindings
  With WSServer.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... properties
  RTCMultiConnection.RTCMultiConnection.Server.Host := txtHost.Text;
  RTCMultiConnection.RTCMultiConnection.Server.Port := StrToInt(txtDefaultPort.Text);

  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
    pnlServerOptions.Enabled := False;
    pnlBrowsers.Enabled := True;
  end;
end;

procedure TfrmServerRTCMultiConnection.btnStopClick(Sender: TObject);
begin
  WSServer.Active := False;
  WSServer.Bindings.Clear;

  if not WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Stopped');
    pnlServerOptions.Enabled := True;
    pnlBrowsers.Enabled := False;
  end;
end;

procedure TfrmServerRTCMultiConnection.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'https';
  vPort := txtDefaultPort.Text;

  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort + GetHTMLPage), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort + GetHTMLPage), '', 0);
  {$ENDIF}
end;

function TfrmServerRTCMultiConnection.GetHTMLPage: string;
begin
  case cboPages.ItemIndex of
    1: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.ScreenSharing;
    2: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.VideoBroadcasting;
    3: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.AudioConferencing;
    else
      result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.VideoConferencing;
  end;
end;

procedure TfrmServerRTCMultiConnection.pageRTCMultiConnectionHTMLTag(Sender: TObject; Tag: TTag; const
    TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
    ReplaceText := txtDefaultPort.Text
  else if TagString = 'host' then
    ReplaceText := txtHost.Text
  else if TagString = 'ssl' then
    ReplaceText := 's';
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCMessage(Connection: TsgcWSConnection; const
    Text: string);
begin
  memoLog.Lines.Add('Message: ' + Connection.IP + ' - ' + Text);
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCSubscription(Connection: TsgcWSConnection;
    const Subscription: string);
begin
  memoLog.Lines.Add('Subscription: ' + Connection.IP + ' - ' + Subscription);
end;

procedure TfrmServerRTCMultiConnection.WSPAppRTCUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('UnSubscription: ' + Connection.IP + ' - ' + Subscription);
end;

end.
```

