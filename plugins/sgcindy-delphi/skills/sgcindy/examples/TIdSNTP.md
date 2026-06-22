# TIdSNTP - Example

Full source of `fSNTPClient.pas` from the **SNTPClient** demo, which uses `TIdSNTP`.

API reference: [TIdSNTP](../reference/api/TIdSNTP.md)
Source demo: `SNTPClient` (file `fSNTPClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy SNTP Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fSNTPClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdUDPBase, IdUDPClient, IdSNTP;

type
  TfrmSNTPClient = class(TForm)
    lblServer: TLabel;
    edtServer: TEdit;
    lblPort: TLabel;
    edtPort: TEdit;
    btnGetTime: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnGetTimeClick(Sender: TObject);
  private
    FSNTP: TIdSNTP;
    procedure DoLog(const aText: string);
  public
  end;

var
  frmSNTPClient: TfrmSNTPClient;

implementation

{$R *.dfm}

procedure TfrmSNTPClient.FormCreate(Sender: TObject);
begin
  FSNTP := TIdSNTP.Create(nil);
end;

procedure TfrmSNTPClient.FormDestroy(Sender: TObject);
begin
  FSNTP.Free;
end;

procedure TfrmSNTPClient.btnGetTimeClick(Sender: TObject);
begin
  try
    FSNTP.Host := edtServer.Text;
    FSNTP.Port := StrToIntDef(edtPort.Text, 123);
    FSNTP.SyncTime;

    DoLog('NTP Server: ' + FSNTP.Host);
    DoLog('Server Time: ' + DateTimeToStr(FSNTP.DateTime));
    DoLog('Local Time: ' + DateTimeToStr(Now));
    DoLog('Adjustment: ' + IntToStr(FSNTP.AdjustmentTime) + ' ms');
    DoLog('Round Trip Delay: ' + IntToStr(FSNTP.RoundTripDelay) + ' ms');
    DoLog('---');
  except
    on E: Exception do
      DoLog('Error: ' + E.Message);
  end;
end;

procedure TfrmSNTPClient.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

