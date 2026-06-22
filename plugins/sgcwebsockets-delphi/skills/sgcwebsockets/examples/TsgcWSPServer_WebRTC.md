# TsgcWSPServer_WebRTC - Example

Full source of `uServerWebRTC.pas` from the **30.WebRTC_Protocol/03.WebRTC** demo, which uses `TsgcWSPServer_WebRTC`.

API reference: [TsgcWSPServer_WebRTC](../reference/api/TsgcWSPServer_WebRTC.md)
Source demo: `30.WebRTC_Protocol/03.WebRTC` (file `uServerWebRTC.pas`)

```pascal
unit uServerWebRTC;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket, StdCtrls,
  ExtCtrls, IdContext, IdCustomHTTPServer, HTTPApp, HTTPProd,
  sgcWebSocket_Protocol_Base_Server, sgcWebSocket_Protocol_WebRTC_Server,
  sgcWebSocket_Protocols, sgcWebSocket_Classes_Indy, sgcBase_Classes,
  sgcSocket_Classes, sgcTCP_Classes;

type
  TfrmServerWebRTC = class(TForm)
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
    pageWebRTC: TPageProducer;
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    pageJQueryMobileCSS: TPageProducer;
    pageJQuery: TPageProducer;
    pageJQueryMobile: TPageProducer;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    WSPWebRTC: TsgcWSPServer_WebRTC;
    txtChannel: TEdit;
    Label4: TLabel;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure pageWebRTCHTMLTag(Sender: TObject; Tag: TTag; const TagString: string;
        TagParams: TStrings; var ReplaceText: string);
    procedure WSPWebRTCConnect(Connection: TsgcWSConnection);
    procedure WSPWebRTCDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSPWebRTCError(Connection: TsgcWSConnection; const Error: string);
    procedure WSPWebRTCMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSPWebRTCSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPWebRTCUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSServerCommandGet(AContext: TIdContext; ARequestInfo:
        TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
  private
    FRequestSSL: Boolean;
    procedure DoOpenBrowser(const aBrowserName: string);
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmServerWebRTC: TfrmServerWebRTC;

implementation

uses
  ShellAPI;

{$R *.dfm}

procedure TfrmServerWebRTC.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServerWebRTC.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServerWebRTC.btnExplorerClick(Sender: TObject);
begin
  DoOpenBrowser('iexplore');
end;

procedure TfrmServerWebRTC.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServerWebRTC.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServerWebRTC.btnStartClick(Sender: TObject);
begin
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  WSServer.SSLOptions.Port := WSServer.Port;

  // ... bindings
  With WSServer.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
    pnlServerOptions.Enabled := False;
    pnlBrowsers.Enabled := True;
  end;
end;

procedure TfrmServerWebRTC.btnStopClick(Sender: TObject);
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

procedure TfrmServerWebRTC.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'https';
  vPort := txtDefaultPort.Text;

  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ENDIF}
end;

procedure TfrmServerWebRTC.pageWebRTCHTMLTag(Sender: TObject; Tag: TTag; const
    TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
      ReplaceText := txtDefaultPort.Text
  else if TagString = 'host' then
    ReplaceText := txtHost.Text;
end;

procedure TfrmServerWebRTC.WSPWebRTCConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSPWebRTCDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSPWebRTCError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerWebRTC.WSPWebRTCMessage(Connection: TsgcWSConnection; const
    Text: string);
begin
  memoLog.Lines.Add('Message: ' + Connection.IP + ' - ' + Text);
  WSPWebRTC.Broadcast(Text, txtChannel.Text);
end;

procedure TfrmServerWebRTC.WSPWebRTCSubscription(Connection: TsgcWSConnection;
    const Subscription: string);
begin
  memoLog.Lines.Add('Subscription: ' + Connection.IP + ' - ' + Subscription);
end;

procedure TfrmServerWebRTC.WSPWebRTCUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('UnSubscription: ' + Connection.IP + ' - ' + Subscription);
end;

procedure TfrmServerWebRTC.WSServerCommandGet(AContext: TIdContext; ARequestInfo:
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
    AResponseInfo.ContentText := pageWebRTC.Content;
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end;
end;

procedure TfrmServerWebRTC.WSServerConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSServerDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSServerError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerWebRTC.WSServerMessage(Connection: TsgcWSConnection; const
    Text: string);
begin
  memoLog.Lines.Add(Connection.IP + ':' + Text);
end;

end.
```

