# TIdDNSResolver - Example

Full source of `fDNSResolver.pas` from the **DNSResolver** demo, which uses `TIdDNSResolver`.

API reference: [TIdDNSResolver](../reference/api/TIdDNSResolver.md)
Source demo: `DNSResolver` (file `fDNSResolver.pas`)

```pascal
{ ***************************************************************************
  sgcIndy DNS Resolver Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fDNSResolver;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdUDPBase, IdUDPClient,
  IdDNSResolver, IdDNSCommon;

type
  TfrmDNSResolver = class(TForm)
    lblDNSServer: TLabel;
    edDNSServer: TEdit;
    lblPort: TLabel;
    edPort: TEdit;
    lblDomain: TLabel;
    edDomain: TEdit;
    lblQueryType: TLabel;
    cbQueryType: TComboBox;
    btnResolve: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnResolveClick(Sender: TObject);
  private
    fDNSResolver: TIdDNSResolver;
    procedure DoLog(const aMessage: string);
  public
  end;

var
  frmDNSResolver: TfrmDNSResolver;

implementation

{$R *.dfm}

procedure TfrmDNSResolver.FormCreate(Sender: TObject);
begin
  fDNSResolver := TIdDNSResolver.Create(nil);
end;

procedure TfrmDNSResolver.FormDestroy(Sender: TObject);
begin
  fDNSResolver.Free;
end;

procedure TfrmDNSResolver.DoLog(const aMessage: string);
begin
  TThread.Queue(nil, procedure
    begin
      memoLog.Lines.Add(aMessage);
    end);
end;

procedure TfrmDNSResolver.btnResolveClick(Sender: TObject);
var
  i: Integer;
  vDomain: string;
begin
  memoLog.Lines.Clear;

  fDNSResolver.Host := edDNSServer.Text;
  fDNSResolver.Port := StrToIntDef(edPort.Text, 53);
  fDNSResolver.QueryResult.Clear;

  vDomain := edDomain.Text;

  case cbQueryType.ItemIndex of
    0:
      fDNSResolver.QueryType := [qtA];
    1:
      fDNSResolver.QueryType := [qtAAAA];
    2:
      fDNSResolver.QueryType := [qtMX];
    3:
      fDNSResolver.QueryType := [qtNS];
    4:
      fDNSResolver.QueryType := [qtCNAME];
    5:
      fDNSResolver.QueryType := [qtTXT];
    6:
      fDNSResolver.QueryType := [qtSOA];
    7:
      fDNSResolver.QueryType := [qtPTR];
  end;

  try
    DoLog('Resolving ' + vDomain + ' (' + cbQueryType.Text + ')...');
    DoLog('');

    fDNSResolver.Resolve(vDomain);

    if fDNSResolver.QueryResult.Count = 0 then
      DoLog('No results found.')
    else
    begin
      for i := 0 to fDNSResolver.QueryResult.Count - 1 do
      begin
        if fDNSResolver.QueryResult[i] is TResultRecord then
          DoLog(TResultRecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TResultRecord(fDNSResolver.QueryResult[i]).IPAddress)
        else if fDNSResolver.QueryResult[i] is TAAAARecord then
          DoLog(TAAAARecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TAAAARecord(fDNSResolver.QueryResult[i]).IPv6Address)
        else if fDNSResolver.QueryResult[i] is TMXRecord then
          DoLog(TMXRecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TMXRecord(fDNSResolver.QueryResult[i]).ExchangeServer +
            ' (Priority: ' + IntToStr(TMXRecord(fDNSResolver.QueryResult[i])
            .Preference) + ')')
        else if fDNSResolver.QueryResult[i] is TNSRecord then
          DoLog(TNSRecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TNSRecord(fDNSResolver.QueryResult[i]).HostName)
        else if fDNSResolver.QueryResult[i] is TCNAMERecord then
          DoLog(TCNAMERecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TCNAMERecord(fDNSResolver.QueryResult[i]).CanonicalName)
        else if fDNSResolver.QueryResult[i] is TTXTRecord then
          DoLog(TTXTRecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TTXTRecord(fDNSResolver.QueryResult[i]).Strings.Text)
        else if fDNSResolver.QueryResult[i] is TSOARecord then
          DoLog(TSOARecord(fDNSResolver.QueryResult[i]).Name +
            ' -> Primary NS: ' + TSOARecord(fDNSResolver.QueryResult[i]).Primary
            + ', Responsible: ' + TSOARecord(fDNSResolver.QueryResult[i])
            .ResponsiblePerson + ', Serial: ' +
            IntToStr(TSOARecord(fDNSResolver.QueryResult[i]).Serial))
        else if fDNSResolver.QueryResult[i] is TPTRRecord then
          DoLog(TPTRRecord(fDNSResolver.QueryResult[i]).Name + ' -> ' +
            TPTRRecord(fDNSResolver.QueryResult[i]).HostName);
      end;
    end;

    DoLog('');
    DoLog('Done. ' + IntToStr(fDNSResolver.QueryResult.Count) +
      ' record(s) found.');
  except
    on E: Exception do
      DoLog('Error: ' + E.Message);
  end;
end;

end.
```

