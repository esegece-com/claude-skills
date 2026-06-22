# TsgcWSPServer_sgc - Example

Full source of `fServer.pas` from the **01.WebSocket_Quick_Start/03.Real_Time_Monitor** demo, which uses `TsgcWSPServer_sgc`.

API reference: [TsgcWSPServer_sgc](../reference/api/TsgcWSPServer_sgc.md)
Source demo: `01.WebSocket_Quick_Start/03.Real_Time_Monitor` (file `fServer.pas`)

```pascal
unit fServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, DB, Grids, DBGrids, DBClient, Math, Activex,
  // sgc
  sgcWebSocket_Server, sgcWebSocket,  sgcWebSocket_Classes,
  sgcWebSocket_Protocols,
  sgcWebSocket_Protocol_sgc_Server, sgcWebSocket_Protocol_Base_Server;

type
  TfrmServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    WSServer: TsgcWebSocketServer;
    pnlServer: TPanel;
    memoLog: TMemo;
    Timer1: TTimer;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    WSServer_sgc: TsgcWSPServer_sgc;
    btnExplorer: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSServer_sgcMessage(Connection: TsgcWSConnection; const Text:
        string);
    procedure WSServer_sgcSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSServer_sgcUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure Timer1Timer(Sender: TObject);
    procedure WSServer_sgcConnect(Connection: TsgcWSConnection);
    procedure WSServer_sgcDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSServer_sgcError(Connection: TsgcWSConnection; const Error: string);
  private
    FCpu: Integer;
    FMemory: Integer;
    FNetwork: Integer;
    procedure DoOpenBrowser(const aBrowserName: string);
    function GetCpu: Integer;
    function GetMemory: Integer;
    function GetNetwork: Integer;
    { Private declarations }
  public
    property Cpu: Integer read GetCpu;
    property Memory: Integer read GetMemory;
    property Network: Integer read GetNetwork;
    { Public declarations }
  end;

var
  frmServer: TfrmServer;

implementation

uses
  ShellAPI;

{$R *.dfm}

procedure TfrmServer.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServer.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServer.btnExplorerClick(Sender: TObject);
begin
  DoOpenBrowser('explorer');
end;

procedure TfrmServer.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServer.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServer.btnStartClick(Sender: TObject);
begin
  if not WSServer.Active then
  begin
    WSServer.Active := True;
    Timer1.Enabled := True;
    memoLog.Lines.Add('#started');
  end;
end;

procedure TfrmServer.btnStopClick(Sender: TObject);
begin
  if WSServer.Active then
  begin
    Timer1.Enabled := False;
    WSServer.Active := False;
    memoLog.Lines.Add('#stopped');
  end;
end;

procedure TfrmServer.DoOpenBrowser(const aBrowserName: string);
begin
  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(ExtractFilePath(Application.ExeName) + 'wsmonitor.html'), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(ExtractFilePath(Application.ExeName) + 'wsmonitor.html'), '', 0);
  {$ENDIF}
end;

function TfrmServer.GetCpu: Integer;
begin
  if FCpu = 0 then
    FCpu := 50
  else if FCpu >= 100 then
    FCpu := 90
  else if FCpu <= 1 then
    FCpu := 10
  else
    FCpu := FCpu + RandomRange(-3, 4);
  Result := FCpu;
end;

function TfrmServer.GetMemory: Integer;
begin
  if FMemory = 0 then
    FMemory := 50
  else if FMemory >= 100 then
    FMemory := 90
  else if FMemory <= 1 then
    FMemory := 10
  else
    FMemory := FMemory + RandomRange(-3, 4);
  Result := FMemory;
end;

function TfrmServer.GetNetwork: Integer;
begin
  if FNetwork = 0 then
    FNetwork := 50
  else if FNetwork >= 100 then
    FNetwork := 90
  else if FNetwork <= 1 then
    FNetwork := 10
  else
    FNetwork := FNetwork + RandomRange(-3, 4);
  Result := FNetwork;
end;

procedure TfrmServer.WSServer_sgcMessage(Connection: TsgcWSConnection;
    const Text: string);
begin
  memoLog.Lines.Add('Message Received (' + Connection.Guid + '): ' + Text);
end;

procedure TfrmServer.WSServer_sgcSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('Subscribed: ' + Connection.Guid + ':' + Subscription);
end;

procedure TfrmServer.WSServer_sgcUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('Unsubscribed: ' + Connection.Guid + ':' + Subscription);
end;

procedure TfrmServer.Timer1Timer(Sender: TObject);
var
  i: Integer;
begin
  if WSServer.Count > 0 then
  begin
    i := RandomRange(1, 5);
    case i of
      1: WSServer_sgc.Publish(IntToStr(cpu), 'cpu');
      2: WSServer_sgc.Publish(IntToStr(memory), 'memory');
      3: WSServer_sgc.Publish(IntToStr(network), 'network');
    end;
  end;
end;

procedure TfrmServer.WSServer_sgcConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.Guid);
end;

procedure TfrmServer.WSServer_sgcDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.Guid);
end;

procedure TfrmServer.WSServer_sgcError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.Guid + ':' + Error);
end;

end.
```

