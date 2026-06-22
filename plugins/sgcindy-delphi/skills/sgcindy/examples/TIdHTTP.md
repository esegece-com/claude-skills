# TIdHTTP - Example

Full source of `FHttpClient.pas` from the **HttpClient** demo, which uses `TIdHTTP`.

API reference: [TIdHTTP](../reference/api/TIdHTTP.md)
Source demo: `HttpClient` (file `FHttpClient.pas`)

```pascal
unit FHttpClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient,
  IdHTTP, IdIOHandler, IdIOHandlerSocket, IdIOHandlerStack, IdSSL,
  IdSSLOpenSSL, IdSSLOpenSSLHeaders, StdCtrls;

type
  TFRMHttpClient = class(TForm)
    IdHTTP1: TIdHTTP;
    btnGoTo: TButton;
    txtURL: TEdit;
    cboOpenSSLAPI: TComboBox;
    Label1: TLabel;
    memoLog: TMemo;
    IdSSLIOHandlerSocketOpenSSL1: TIdSSLIOHandlerSocketOpenSSL;
    procedure btnGoToClick(Sender: TObject);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfo(const AMsg: String);
  private

  public
    { Public declarations }
  end;

var
  FRMHttpClient: TFRMHttpClient;

implementation



{$R *.dfm}

procedure TFRMHttpClient.btnGoToClick(Sender: TObject);
var
  oStream: TStringStream;
begin
  case cboOpenSSLAPI.ItemIndex of
    0:
      begin
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_0;
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_2;
      end;
    1:
      begin
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_1;
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_3;
      end;
    2:
      begin
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_3_0;
        IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_3;
      end;
  end;

  oStream := TStringStream.Create('');
  Try
    IdHTTP1.Get(txtURL.Text, oStream);
    btnGoTo.Enabled := False;
  Finally
    FreeAndNil(oStream);
  End;
end;

procedure TFRMHttpClient.IdSSLIOHandlerSocketOpenSSL1StatusInfo(
  const AMsg: String);
begin
  if Assigned(memoLog) then
    memoLog.Lines.Add(AMsg);
end;

end.
```

