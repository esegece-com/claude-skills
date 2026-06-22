# TsgcWebSocketProxyServer - Example

Full source of `fServerProxy.pas` from the **04.WebSocket_Other_Samples/05.Proxy_Server** demo, which uses `TsgcWebSocketProxyServer`.

API reference: [TsgcWebSocketProxyServer](../reference/api/TsgcWebSocketProxyServer.md)
Source demo: `04.WebSocket_Other_Samples/05.Proxy_Server` (file `fServerProxy.pas`)

```pascal
unit fServerProxy;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, DB, Grids, DBGrids, DBClient,
  // sgc
  sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket_Server_Proxy,
  sgcWebSocket;

type
  TfrmServerProxy = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    pnlServer: TPanel;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    btnExplorer: TButton;
    WSServer: TsgcWebSocketProxyServer;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
  private
    procedure DoOpenBrowser(const aBrowserName: string);
  end;

var
  frmServerProxy: TfrmServerProxy;

implementation

uses
  ShellAPI;

{$R *.dfm}


procedure TfrmServerProxy.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServerProxy.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServerProxy.btnExplorerClick(Sender: TObject);
begin
  DoOpenBrowser('explorer');
end;

procedure TfrmServerProxy.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServerProxy.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServerProxy.btnStartClick(Sender: TObject);
begin
  if not WSServer.Active then
  begin
    WSServer.Active := True;
    btnStart.Enabled := False;
    btnStop.Enabled := True;
  end;
end;

procedure TfrmServerProxy.btnStopClick(Sender: TObject);
begin
  if WSServer.Active then
  begin
    WSServer.Active := False;
    btnStart.Enabled := True;
    btnStop.Enabled := False;
  end;
end;

procedure TfrmServerProxy.DoOpenBrowser(const aBrowserName: string);
begin
  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(ExtractFilePath(Application.ExeName) + 'wsproxy.html'), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(ExtractFilePath(Application.ExeName) + 'wsproxy.html'), '', 0);
  {$ENDIF}
end;

end.
```

