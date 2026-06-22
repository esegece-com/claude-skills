# TsgcWSPServer_Dataset - Example

Full source of `fServer.pas` from the **02.WebSocket_Protocols/05.DataSet_Quotes_Protocol** demo, which uses `TsgcWSPServer_Dataset`.

API reference: [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md)
Source demo: `02.WebSocket_Protocols/05.DataSet_Quotes_Protocol` (file `fServer.pas`)

```pascal
unit fServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, DB, Grids, DBGrids, DBClient, Math, Activex,
  // sgc
  sgcWebSocket_Server, sgcWebSocket,  sgcWebSocket_Classes, uDMQuotes,
  sgcWebSocket_Protocols,
  sgcWebSocket_Protocol_sgc_Server, sgcWebSocket_Protocol_Dataset_Server,
  sgcWebSocket_Protocol_Base_Server, sgcWebSocket_Classes_Indy;

type
  TfrmServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    WSServer: TsgcWebSocketServer;
    pnlServer: TPanel;
    memoLog: TMemo;
    pnlQuotes: TPanel;
    DBGrid1: TDBGrid;
    dsQuotes: TDataSource;
    Timer1: TTimer;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    WSPServer_dataset: TsgcWSPServer_Dataset;
    btnExplorer: TButton;
    procedure btnChromeClick(Sender: TObject);
    procedure btnExplorerClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure Timer1Timer(Sender: TObject);
    procedure WSPServer_datasetConnect(Connection: TsgcWSConnection);
    procedure WSPServer_datasetDisconnect(Connection: TsgcWSConnection; Code:
        Integer);
    procedure WSPServer_datasetError(Connection: TsgcWSConnection; const Error:
        string);
    procedure WSPServer_datasetMessage(Connection: TsgcWSConnection; const Text:
        string);
    procedure WSPServer_datasetSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPServer_datasetUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
  private
    FDMQuotes: TDMQuotes;
    procedure DoLastQuotes;
    procedure DoOpenBrowser(const aBrowserName: string);
    procedure DoStartQuotes;
    function GetDMQuotes: TDMQuotes;
    { Private declarations }
  public
    property DMQuotes: TDMQuotes read GetDMQuotes write FDMQuotes;
    { Public declarations }
  end;

var
  frmServer: TfrmServer;

const
  CS_BLOCK = 20;

implementation

uses
  ShellAPI;

{$R *.dfm}

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

procedure TfrmServer.FormCreate(Sender: TObject);
begin
  dsQuotes.DataSet := DMQuotes.cdsQuotes;
  WSPServer_dataset.Dataset := DMQuotes.cdsQuotes;
  btnStart.Click;
end;

procedure TfrmServer.btnStartClick(Sender: TObject);
begin
  WSServer.Active := True;
  DoStartQuotes;
  Timer1.Enabled := True;
end;

procedure TfrmServer.btnStopClick(Sender: TObject);
begin
  Timer1.Enabled := False;
  WSServer.Active := False;
end;

procedure TfrmServer.DoLastQuotes;
begin
  Randomize;

  With GetDMQuotes.cdsQuotes do
  begin
    if Findkey([RandomRange(1, CS_BLOCK)]) then
    begin
      Edit;
      FieldByName('LAST').AsFloat := RandomRange(FieldByName('LAST').AsInteger - CS_BLOCK, FieldByName('LAST').AsInteger + CS_BLOCK);
      if FieldByName('LAST').AsFloat > FieldByName('HIGH').AsFloat then
        FieldByName('HIGH').AsFloat := FieldByName('LAST').AsFloat;
      if FieldByName('LAST').AsFloat < FieldByName('LOW').AsFloat then
        FieldByName('LOW').AsFloat := FieldByName('LAST').AsFloat;
      Post;
    end;
  end;
end;

procedure TfrmServer.DoOpenBrowser(const aBrowserName: string);
begin
  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
      PWideChar(ExtractFilePath(Application.ExeName) + 'wsquotes.html'), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
      PAnsiChar(ExtractFilePath(Application.ExeName) + 'wsquotes.html'), '', 0);
  {$ENDIF}
end;

procedure TfrmServer.DoStartQuotes;
var
  i, j: Integer;
begin
  Randomize;
  GetDMQuotes.cdsQuotes.EmptyDataSet;

  for i := 1 to CS_BLOCK do
  begin
    j := RandomRange(-5000, 5000);
    With GetDMQuotes.cdsQuotes do
    begin
      Append;
      FieldByName('ID').AsInteger := i;
      FieldByName('NAME').AsString := 'Symbol ' + IntToStr(i);
      FieldByName('EXCHANGE').AsString := 'Nasdaq';

      FieldByName('OPEN').AsFloat := RandomRange(8300, 8320) + j;
      FieldByName('HIGH').AsFloat := RandomRange(8300, 8400) + j;
      FieldByName('LOW').AsFloat := RandomRange(8200, 8300) + j;
      FieldByName('LAST').AsFloat := RandomRange(8250, 8280) + j;
      Post;
    end;
  end;
end;

function TfrmServer.GetDMQuotes: TDMQuotes;
begin
  if not Assigned(FDMQuotes) then
    FDMQuotes := TDMQuotes.Create(self);
  Result := FDMQuotes;
end;

procedure TfrmServer.Timer1Timer(Sender: TObject);
begin
  DoLastQuotes;
end;

procedure TfrmServer.WSPServer_datasetConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.Guid);
end;

procedure TfrmServer.WSPServer_datasetDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.Guid);
end;

procedure TfrmServer.WSPServer_datasetError(Connection: TsgcWSConnection; const
    Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.Guid + ':' + Error);
end;

procedure TfrmServer.WSPServer_datasetMessage(Connection: TsgcWSConnection;
    const Text: string);
begin
  memoLog.Lines.Add('Message Received (' + Connection.Guid + '): ' + Text);
end;

procedure TfrmServer.WSPServer_datasetSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('Subscribed: ' + Connection.Guid + ':' + Subscription);
end;

procedure TfrmServer.WSPServer_datasetUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('Unsubscribed: ' + Connection.Guid + ':' + Subscription);
end;

end.
```

