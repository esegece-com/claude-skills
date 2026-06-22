# TIdWhois - Example

Full source of `fWhoisClient.pas` from the **WhoisClient** demo, which uses `TIdWhois`.

API reference: [TIdWhois](../reference/api/TIdWhois.md)
Source demo: `WhoisClient` (file `fWhoisClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy Whois Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fWhoisClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient, IdWhois;

type
  TfrmWhoisClient = class(TForm)
    lblServer: TLabel;
    lblPort: TLabel;
    lblDomain: TLabel;
    txtServer: TEdit;
    txtPort: TEdit;
    txtDomain: TEdit;
    btnLookup: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnLookupClick(Sender: TObject);
  private
    Whois: TIdWhois;
    procedure DoLog(const aMessage: string);
  public
  end;

var
  frmWhoisClient: TfrmWhoisClient;

implementation

{$R *.dfm}

procedure TfrmWhoisClient.FormCreate(Sender: TObject);
begin
  Whois := TIdWhois.Create(nil);
end;

procedure TfrmWhoisClient.FormDestroy(Sender: TObject);
begin
  Whois.Free;
end;

procedure TfrmWhoisClient.btnLookupClick(Sender: TObject);
var
  vResult: string;
begin
  try
    Whois.Host := txtServer.Text;
    Whois.Port := StrToInt(txtPort.Text);
    vResult := Whois.Whois(txtDomain.Text);
    DoLog(vResult);
  except
    on E: Exception do
      DoLog('Error: ' + E.Message);
  end;
end;

procedure TfrmWhoisClient.DoLog(const aMessage: string);
begin
  memoLog.Lines.Add(aMessage);
end;

end.
```

