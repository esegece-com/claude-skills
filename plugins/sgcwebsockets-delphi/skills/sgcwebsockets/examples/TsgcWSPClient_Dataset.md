# TsgcWSPClient_Dataset - Example

Full source of `fClient.pas` from the **02.WebSocket_Protocols/05.DataSet_Quotes_Protocol** demo, which uses `TsgcWSPClient_Dataset`.

API reference: [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md)
Source demo: `02.WebSocket_Protocols/05.DataSet_Quotes_Protocol` (file `fClient.pas`)

```pascal
unit fClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  Grids, DBGrids, ExtCtrls, Activex, uDMQuotes, DB,
  sgcWebSocket_Protocols, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocol_sgc_Client, sgcWebSocket_Protocol_Dataset_Client,
  sgcWebSocket_Classes_Indy;

type
  TfrmClientQuotes = class(TForm)
    WSClient: TsgcWebSocketClient;
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    DBGrid1: TDBGrid;
    dsGrid: TDataSource;
    WSPClient_dataset: TsgcWSPClient_Dataset;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSPClient_datasetConnect(Connection: TsgcWSConnection);
    procedure WSPClient_datasetDisconnect(Connection: TsgcWSConnection; Code:
        Integer);
    procedure WSPClient_datasetError(Connection: TsgcWSConnection; const Error:
        string);
    procedure WSPClient_datasetSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPClient_datasetUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
  private
    FDMQuotes: TDMQuotes;
    function GetDMQuotes: TDMQuotes;
    { Private declarations }
  public
    property DMQuotes: TDMQuotes read GetDMQuotes write FDMQuotes;
    { Public declarations }
  end;

var
  frmClientQuotes: TfrmClientQuotes;

implementation

{$R *.dfm}

procedure TfrmClientQuotes.FormCreate(Sender: TObject);
begin
  WSPClient_dataset.Dataset := DMQuotes.cdsQuotes;
end;

procedure TfrmClientQuotes.btnStartClick(Sender: TObject);
begin
  WSClient.Active := True;
end;

procedure TfrmClientQuotes.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;
end;

function TfrmClientQuotes.GetDMQuotes: TDMQuotes;
begin
  if not Assigned(FDMQuotes) then
  begin
    FDMQuotes := TDMQuotes.Create(self);
    dsGrid.DataSet := FDMQuotes.cdsQuotes;
  end;
  Result := FDMQuotes;
end;

procedure TfrmClientQuotes.WSPClient_datasetConnect(Connection:
    TsgcWSConnection);
begin
  memoLog.Lines.Add('#connected');
end;

procedure TfrmClientQuotes.WSPClient_datasetDisconnect(Connection:
    TsgcWSConnection; Code: Integer);
begin
  memoLog.Lines.Add('#disconnected: ' + IntToStr(Code));
end;

procedure TfrmClientQuotes.WSPClient_datasetError(Connection: TsgcWSConnection;
    const Error: string);
begin
  memoLog.Lines.Add('#error: ' + Error);
end;

procedure TfrmClientQuotes.WSPClient_datasetSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('#subscription: ' + Subscription);
end;

procedure TfrmClientQuotes.WSPClient_datasetUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('#unsubscription: ' + Subscription);
end;

end.
```

