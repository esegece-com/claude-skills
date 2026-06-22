# TsgcWSPServer_E2EE - Example

Full source of `uServerE2EE.pas` from the **02.WebSocket_Protocols/12.E2EE** demo, which uses `TsgcWSPServer_E2EE`.

API reference: [TsgcWSPServer_E2EE](../reference/api/TsgcWSPServer_E2EE.md)
Source demo: `02.WebSocket_Protocols/12.E2EE` (file `uServerE2EE.pas`)

```pascal
unit uServerE2EE;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket, StdCtrls,
  ExtCtrls, IdContext, IdCustomHTTPServer, HTTPApp, HTTPProd,
  sgcWebSocket_Classes_Indy, sgcBase_Classes, sgcSocket_Classes, sgcTCP_Classes,
  sgcWebSocket_Types, sgcWebSocket_Protocol_Base_Server,
  sgcWebSocket_Protocols, sgcWebSocket_Protocol_E2EE_Server;

type
  TfrmServerE2EE = class(TForm)
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    pnlServerActive: TPanel;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    Default: TLabel;
    chkSSL: TCheckBox;
    WSPE2EE: TsgcWSPServer_E2EE;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSPE2EEE2EEMessageIn(Sender: TObject; const aText: string);
    procedure WSPE2EEE2EEMessageOut(Sender: TObject; const aText: string);
  private
    { Private declaraions }
  public
    procedure DoLog(const aText: string);
    { Public declarations }
  end;

var
  frmServerE2EE: TfrmServerE2EE;

implementation

{$R *.dfm}

procedure TfrmServerE2EE.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServerE2EE.btnStartClick(Sender: TObject);
begin
  WSServer.Port := StrToInt(txtDefaultPort.text);
  WSServer.SSL := chkSSL.Checked;
  if chkSSL.Checked then
    WSServer.SSLOptions.Port := WSServer.Port;

  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
    DoLog('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
    if chkSSL.checked then
      DoLog('#SSL Enabled');
    pnlServerOptions.Enabled := False;
  end;
end;

procedure TfrmServerE2EE.btnStopClick(Sender: TObject);
begin
  WSServer.Active := False;
  WSServer.Bindings.Clear;

  if not WSServer.Active then
  begin
    DoLog('#Server Stopped');
    pnlServerOptions.Enabled := True;
  end;
end;

procedure TfrmServerE2EE.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
         memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmServerE2EE.WSPE2EEE2EEMessageIn(Sender: TObject; const aText:
    string);
begin
  DoLog('<-- ' + aText);
end;

procedure TfrmServerE2EE.WSPE2EEE2EEMessageOut(Sender: TObject; const aText:
    string);
begin
  DoLog('--> ' + aText);
end;

end.
```

