# TsgcWSPServer_WAMP - Example

Full source of `uServerWAMP.pas` from the **02.WebSocket_Protocols/04.WAMP_Protocol** demo, which uses `TsgcWSPServer_WAMP`.

API reference: [TsgcWSPServer_WAMP](../reference/api/TsgcWSPServer_WAMP.md)
Source demo: `02.WebSocket_Protocols/04.WAMP_Protocol` (file `uServerWAMP.pas`)

```pascal
unit uServerWAMP;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket, StdCtrls,
  ExtCtrls, IdContext, IdCustomHTTPServer, HTTPApp, HTTPProd,
  sgcWebSocket_Protocol_Base_Server, sgcWebSocket_Protocol_WAMP_Server,
  sgcWebSocket_Protocols, sgcWebSocket_Classes_Indy, sgcBase_Classes,
  sgcTCP_Classes;

type
  TfrmServerWAMP = class(TForm)
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    btnExplorer: TButton;
    pnlServerActive: TPanel;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    pnlBrowsers: TPanel;
    pageWAMP: TPageProducer;
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    pageJQueryMobileCSS: TPageProducer;
    pageJQuery: TPageProducer;
    pageJQueryMobile: TPageProducer;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    Default: TLabel;
    WSPWAMP: TsgcWSPServer_WAMP;
    Label4: TLabel;
    chkFlash: TCheckBox;
    chkSSE: TCheckBox;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure chkFlashClick(Sender: TObject);
    procedure chkSSEClick(Sender: TObject);
    procedure pageWAMPHTMLTag(Sender: TObject; Tag: TTag; const TagString: string;
        TagParams: TStrings; var ReplaceText: string);
    procedure WSPWAMPBeforeCancelCall(Connection: TsgcWSConnection; const CallId:
        string; var Cancel: Boolean);
    procedure WSPWAMPCall(Connection: TsgcWSConnection; const CallId, ProcUri,
        Arguments: string);
    procedure WSPWAMPConnect(Connection: TsgcWSConnection);
    procedure WSPWAMPDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSPWAMPError(Connection: TsgcWSConnection; const Error: string);
    procedure WSPWAMPMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSPWAMPPrefix(Connection: TsgcWSConnection; const Key, Value: string);
    procedure WSPWAMPSubscription(Connection: TsgcWSConnection; const Subscription:
        string);
    procedure WSPWAMPUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSServerCommandGet(AContext: TIdContext; ARequestInfo:
        TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
  private
    FRequestSSL: Boolean;
    procedure DoCall(const CallId, ProcURI, Arguments: string);
    procedure DoOpenBrowser(const aBrowserName: string);
    { Private declarations }
  protected
  public
    { Public declarations }
  end;

  TTimerThread = class(TThread)
  private
    FCallId: String;
    FProtocol: TsgcWSPServer_WAMP;
  public
    procedure Execute; override;
  public
    property CallId: String read FCallId write FCallId;
    property Protocol: TsgcWSPServer_WAMP read FProtocol write FProtocol;
  end;

var
  frmServerWAMP: TfrmServerWAMP;

implementation

uses
  ShellAPI;

{$R *.dfm}

procedure TfrmServerWAMP.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServerWAMP.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServerWAMP.btnExplorerClick(Sender: TObject);
begin
  DoOpenBrowser('iexplore');
end;

procedure TfrmServerWAMP.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServerWAMP.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServerWAMP.btnStartClick(Sender: TObject);
begin
  WSServer.Port := StrToInt(txtDefaultPort.Text);

  // ... bindings
  With WSServer.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  if chkFlash.Checked then
  begin
    With WSServer.Bindings.Add do
    begin
      Port := 843;
      IP := txtHost.Text;
    end;
  end;

  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
    if chkFlash.checked then
      memoLog.Lines.Add('#Flash FallBack Enabled');
    if chkSSE.checked then
      memoLog.Lines.Add('#SSE FallBack Enabled');
    pnlServerOptions.Enabled := False;
    pnlBrowsers.Enabled := True;
  end;
end;

procedure TfrmServerWAMP.btnStopClick(Sender: TObject);
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

procedure TfrmServerWAMP.chkFlashClick(Sender: TObject);
begin
  WSServer.FallBack.Flash.Enabled := chkFlash.Checked;
end;

procedure TfrmServerWAMP.chkSSEClick(Sender: TObject);
begin
  WSServer.FallBack.ServerSentEvents.Enabled := chkSSE.Checked;
end;

procedure TfrmServerWAMP.DoCall(const CallId, ProcURI, Arguments: string);
var
  vInteger: Integer;
  oThread: TTimerThread;
begin
  if ProcURI = 'sgc:calculate' then
  begin
    TryStrToInt(Arguments, vInteger);
    WSPWAMP.CallResult(CallId, IntToStr(vInteger * 50));
  end
  else if ProcURI = 'sgc:timer' then
  begin
    oThread := TTimerThread.Create(True);
    oThread.FreeOnTerminate := True;
    oThread.CallId := CallId;
    oThread.Protocol := WSPWAMP;
    oThread.Start;
  end
  else
    WSPWAMP.CallError(CallId, ProcURI, 'Call method not found!');
end;

procedure TfrmServerWAMP.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'http';
  vPort := txtDefaultPort.Text;

  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ENDIF}
end;

procedure TfrmServerWAMP.pageWAMPHTMLTag(Sender: TObject; Tag: TTag; const
    TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
    ReplaceText := txtDefaultPort.Text
  else if TagString = 'host' then
    ReplaceText := txtHost.Text;
end;

procedure TfrmServerWAMP.WSPWAMPBeforeCancelCall(Connection: TsgcWSConnection;
    const CallId: string; var Cancel: Boolean);
begin
  memoLog.Lines.Add('Cancel Call: ' + CallId);
end;

procedure TfrmServerWAMP.WSPWAMPCall(Connection: TsgcWSConnection; const
    CallId, ProcUri, Arguments: string);
begin
  memoLog.Lines.Add('Call: ' + CallId + ' - ' + ProcUri + ' - ' + Arguments);

  // ... process remote call
  DoCall(CallId, ProcURI, Arguments);
end;

procedure TfrmServerWAMP.WSPWAMPConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerWAMP.WSPWAMPDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerWAMP.WSPWAMPError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerWAMP.WSPWAMPMessage(Connection: TsgcWSConnection; const
    Text: string);
begin
  memoLog.Lines.Add(Connection.IP + ':' + Text);
end;

procedure TfrmServerWAMP.WSPWAMPPrefix(Connection: TsgcWSConnection; const Key,
    Value: string);
begin
  memoLog.Lines.Add('Prefix: ' + Key + ' - ' + Value);
end;

procedure TfrmServerWAMP.WSPWAMPSubscription(Connection: TsgcWSConnection;
    const Subscription: string);
begin
  memoLog.Lines.Add('Subscribe: ' + Subscription);
end;

procedure TfrmServerWAMP.WSPWAMPUnSubscription(Connection: TsgcWSConnection;
    const Subscription: string);
begin
  memoLog.Lines.Add('UnSubscribe: ' + Subscription);
end;

procedure TfrmServerWAMP.WSServerCommandGet(AContext: TIdContext; ARequestInfo:
    TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
begin
  if ARequestInfo.Document = '/jquery.mobile.css' then
  begin
    AResponseInfo.ContentText := pageJQueryMobileCSS.Content;
    AResponseInfo.ContentType := 'text/css';
    AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.js' then
  begin
    AResponseInfo.ContentText := pageJQuery.Content;
    AResponseInfo.ContentType := 'text/javascript';
    AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.mobile.js' then
  begin
    AResponseInfo.ContentText := pageJQueryMobile.Content;
    AResponseInfo.ContentType := 'text/javascript';
    AResponseInfo.ResponseNo := 200;
  end
  else
  begin
    if AContext.Connection.Socket.Binding.Port = WSServer.SSLOptions.Port then
      FRequestSSL := True
    else
      FRequestSSL := False;
    AResponseInfo.ContentText := pageWAMP.Content;
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end;
end;

procedure TTimerThread.Execute;
var
  i: integer;
begin
  inherited;
  i := 1;
  repeat
    if i = 20 then
    begin
      TThread.Queue(nil,
      procedure
      begin
        Protocol.CallResult(CallId, FormatDateTime('yyyymmdd hh:nn:ss', Now))
      end);
    end
    else
      TThread.Queue(nil,
      procedure
      begin
        Protocol.CallProgressResult(CallId, FormatDateTime('yyyymmdd hh:nn:ss', Now))
      end);
    sleep(1000);
    inc(i);
  until
    i > 20;

  Terminate;
end;

end.
```

