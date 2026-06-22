# TsgcWSPServer_AppRTC - Example

Full source of `uServerAppRTC.pas` from the **30.WebRTC_Protocol/01.AppRTC** demo, which uses `TsgcWSPServer_AppRTC`.

API reference: [TsgcWSPServer_AppRTC](../reference/api/TsgcWSPServer_AppRTC.md)
Source demo: `30.WebRTC_Protocol/01.AppRTC` (file `uServerAppRTC.pas`)

```pascal
unit uServerAppRTC;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils,
  HTTPApp, HTTPProd,
  // indy
  IdContext, IdCustomHTTPServer,
  // sgc
  sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket,
  sgcWebSocket_Protocol_Base_Server, sgcBase_Helpers,
  sgcWebSocket_Protocols, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Protocol_AppRTC_Server, sgcBase_Classes, sgcTCP_Classes;

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
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    WSPAppRTC: TsgcWSPServer_AppRTC;
    pageAppRTC: TPageProducer;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure pageAppRTCHTMLTag(Sender: TObject; Tag: TTag; const TagString: string;
        TagParams: TStrings; var ReplaceText: string);
    procedure WSPAppRTCConnect(Connection: TsgcWSConnection);
    procedure WSPAppRTCDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSPAppRTCError(Connection: TsgcWSConnection; const Error: string);
    procedure WSPAppRTCMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSPAppRTCSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPAppRTCUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSServerCommandGet(AContext: TIdContext; ARequestInfo:
        TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
  private
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

  // ... bindings
  With WSServer.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... properties
  WSPAppRTC.AppRTC.RoomLink := 'https://' + txtHost.Text + ':' + txtDefaultPort.Text + '/r/';
  WSPAppRTC.AppRTC.WebSocketURL := 'wss://' + txtHost.Text + ':' + txtDefaultPort.Text;

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

procedure TfrmServerWebRTC.pageAppRTCHTMLTag(Sender: TObject; Tag: TTag; const
    TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
    ReplaceText := txtDefaultPort.Text
  else if TagString = 'host' then
    ReplaceText := txtHost.Text
  else if TagString = 'ssl' then
    ReplaceText := 's';
end;

procedure TfrmServerWebRTC.WSPAppRTCConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSPAppRTCDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerWebRTC.WSPAppRTCError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerWebRTC.WSPAppRTCMessage(Connection: TsgcWSConnection; const
    Text: string);
begin
  memoLog.Lines.Add('Message: ' + Connection.IP + ' - ' + Text);
end;

procedure TfrmServerWebRTC.WSPAppRTCSubscription(Connection: TsgcWSConnection;
    const Subscription: string);
begin
  memoLog.Lines.Add('Subscription: ' + Connection.IP + ' - ' + Subscription);
end;

procedure TfrmServerWebRTC.WSPAppRTCUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('UnSubscription: ' + Connection.IP + ' - ' + Subscription);
end;

procedure TfrmServerWebRTC.WSServerCommandGet(AContext: TIdContext; ARequestInfo:
    TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
var
  oList: TStringList;
begin
  if ARequestInfo.Document = '/' then
  begin
    AResponseInfo.ContentText := pageAppRTC.Content;
    AResponseInfo.ContentText := sgcStringReplace(pageAppRTC.Content, '{%room%}', '');
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end
  else if LeftStr(UpperCase(ARequestInfo.Document), 2) = '/R' then
  begin
    oList := TStringList.Create;
    Try
      oList.Delimiter := '/';
      oList.DelimitedText := ARequestInfo.Document;
      AResponseInfo.ContentText := sgcStringReplace(pageAppRTC.Content, '{%room%}', 'roomId: ' + quotedStr(oList[oList.Count - 1]) + ', roomLink: ' + quotedStr(ARequestInfo.Document) + ',');
    Finally
      FreeAndNil(oList);
    End;
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end
  else
    AResponseInfo.ResponseNo := 404;
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

