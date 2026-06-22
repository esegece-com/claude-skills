# TsgcWSPServer_Presence - Example

Full source of `FPresenceServer.pas` from the **02.WebSocket_Protocols/03.Presence_Protocol** demo, which uses `TsgcWSPServer_Presence`.

API reference: [TsgcWSPServer_Presence](../reference/api/TsgcWSPServer_Presence.md)
Source demo: `02.WebSocket_Protocols/03.Presence_Protocol` (file `FPresenceServer.pas`)

```pascal
unit FPresenceServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, sgcWebSocket_Classes, sgcWebSocket_Protocol_Base_Server,
  sgcWebSocket_Protocol_Presence_Server, sgcWebSocket_Protocols,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcWebSocket_Protocol_Presence_Message, HTTPApp, HTTPProd, IdContext, IdCustomHTTPServer,
  sgcBase_Classes, sgcTCP_Classes;

type
  TForm16 = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    txtPort: TEdit;
    Label1: TLabel;
    Presence: TsgcWSPServer_Presence;
    ListBox1: TListBox;
    Label2: TLabel;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    btnExplorer: TButton;
    txtHost: TEdit;
    Label3: TLabel;
    Server: TsgcWebSocketHTTPServer;
    pagePresence: TPageProducer;
    pageJQueryMobile: TPageProducer;
    pageJQuery: TPageProducer;
    pageJQueryMobileCSS: TPageProducer;
    chkBase64: TCheckBox;
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure pagePresenceHTMLTag(Sender: TObject; Tag: TTag; const TagString:
        string; TagParams: TStrings; var ReplaceText: string);
    procedure PresenceNewMember(aConnection: TsgcWSConnection; const aMember:
        TsgcWSPresenceMember);
    procedure PresenceRemoveMember(aConnection: TsgcWSConnection; aMember:
        TsgcWSPresenceMember);
    procedure ServerCommandGet(AContext: TIdContext; ARequestInfo:
        TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure ServerShutdown(Sender: TObject);
    procedure ServerStartup(Sender: TObject);
  private
    procedure DoOpenBrowser(const aBrowserName: string);
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form16: TForm16;

implementation

uses
  sgcWebSocket_Helpers,
  ShellAPI;

{$R *.dfm}

procedure TForm16.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TForm16.btnExplorerClick(Sender: TObject);
begin
  DoOpenBrowser('iexplore');
end;

procedure TForm16.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TForm16.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TForm16.btnStartClick(Sender: TObject);
begin
  Presence.EncodeBase64 := chkBase64.Checked;
  Server.Port := StrToInt(txtPort.Text);
  Server.Active := True;
end;

procedure TForm16.btnStopClick(Sender: TObject);
begin
  Server.Active := False;
end;

procedure TForm16.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'http';
  vPort := txtPort.Text;

  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
  {$ENDIF}
end;

procedure TForm16.pagePresenceHTMLTag(Sender: TObject; Tag: TTag; const
    TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
    ReplaceText := txtPort.Text
  else if TagString = 'host' then
    ReplaceText := txtHost.Text
  else if TagString = 'b64' then
  begin
    if Presence.EncodeBase64 then
      ReplaceText := 'true'
    else
      ReplaceText := 'false';
  end;
end;

procedure TForm16.PresenceNewMember(aConnection: TsgcWSConnection; const
    aMember: TsgcWSPresenceMember);
begin
  listBox1.Items.Add(aMember.Name);
end;

procedure TForm16.PresenceRemoveMember(aConnection: TsgcWSConnection; aMember:
    TsgcWSPresenceMember);
begin
  listBox1.Items.Delete(listBox1.Items.IndexOf(aMember.Name));
end;

procedure TForm16.ServerCommandGet(AContext: TIdContext; ARequestInfo:
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
    AResponseInfo.ContentText := pagePresence.Content;
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end;
end;

procedure TForm16.ServerShutdown(Sender: TObject);
begin
  if btnStart <> nil then
  begin
    btnStart.Enabled := True;
    btnStop.Enabled := False;
  end;
end;

procedure TForm16.ServerStartup(Sender: TObject);
begin
  btnStart.Enabled := False;
  btnStop.Enabled := True;
end;

end.
```

