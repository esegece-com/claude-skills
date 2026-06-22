# TIdHTTPServer - Example

Full source of `fHttpServer.pas` from the **HttpServer** demo, which uses `TIdHTTPServer`.

API reference: [TIdHTTPServer](../reference/api/TIdHTTPServer.md)
Source demo: `HttpServer` (file `fHttpServer.pas`)

```pascal
{ ***************************************************************************
  sgcIndy HTTP Server Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fHttpServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdCustomTCPServer, IdCustomHTTPServer,
  IdHTTPServer, IdContext, IdIOHandler, IdIOHandlerSocket, IdIOHandlerStack,
  IdSSL, IdSSLOpenSSL, IdSSLOpenSSLHeaders;

type
  TfrmHttpServer = class(TForm)
    lblPort: TLabel;
    lblOpenSSL: TLabel;
    lblCertFile: TLabel;
    lblKeyFile: TLabel;
    txtPort: TEdit;
    chkTLS: TCheckBox;
    cboOpenSSLAPI: TComboBox;
    txtCertFile: TEdit;
    txtKeyFile: TEdit;
    btnStart: TButton;
    btnStop: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
  private
    fHttpServer: TIdHTTPServer;
    FSSLHandler: TIdSSLIOHandlerSocketOpenSSL;
    procedure OnCommandGet(AContext: TIdContext;
      ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure DoLog(const aMsg: string);
  public
  end;

var
  frmHttpServer: TfrmHttpServer;

implementation

{$R *.dfm}

procedure TfrmHttpServer.FormCreate(Sender: TObject);
begin
  fHttpServer := TIdHTTPServer.Create(nil);
  fHttpServer.OnCommandGet := OnCommandGet;
  FSSLHandler := TIdSSLIOHandlerSocketOpenSSL.Create(nil);
end;

procedure TfrmHttpServer.FormDestroy(Sender: TObject);
begin
  fHttpServer.Free;
  FSSLHandler.Free;
end;

procedure TfrmHttpServer.btnStartClick(Sender: TObject);
begin
  fHttpServer.DefaultPort := StrToIntDef(txtPort.Text, 8080);

  if chkTLS.Checked then
  begin
    case cboOpenSSLAPI.ItemIndex of
      0:
        IdSSLOpenSSLHeaders.IdOpenSSLSetLibPath('',
          TIdOpenSSLAPIVersion.OSSlv10);
      1:
        IdSSLOpenSSLHeaders.IdOpenSSLSetLibPath('',
          TIdOpenSSLAPIVersion.OSSlv11);
      2:
        IdSSLOpenSSLHeaders.IdOpenSSLSetLibPath('',
          TIdOpenSSLAPIVersion.OSSlv30);
    end;

    FSSLHandler.SSLOptions.CertFile := txtCertFile.Text;
    FSSLHandler.SSLOptions.KeyFile := txtKeyFile.Text;
    FSSLHandler.SSLOptions.Mode := sslmServer;
    fHttpServer.IOHandler := FSSLHandler;
  end
  else
    fHttpServer.IOHandler := nil;

  fHttpServer.Active := True;
  DoLog('Server started on port ' + txtPort.Text);
end;

procedure TfrmHttpServer.btnStopClick(Sender: TObject);
begin
  fHttpServer.Active := False;
  DoLog('Server stopped');
end;

procedure TfrmHttpServer.OnCommandGet(AContext: TIdContext;
  ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
var
  vMsg: string;
begin
  vMsg := ARequestInfo.Command + ' ' + ARequestInfo.URI;
  TThread.Queue(nil, procedure
    begin
      DoLog(vMsg);
    end);

  AResponseInfo.ContentType := 'text/html';
  AResponseInfo.ContentText :=
    '<html><body><h1>eSeGeCe sgcIndy HTTP Server</h1>' + '<p>Request: ' +
    ARequestInfo.Document + '</p>' + '<p>Method: ' + ARequestInfo.Command +
    '</p></body></html>';
end;

procedure TfrmHttpServer.DoLog(const aMsg: string);
begin
  TThread.Queue(nil, procedure
    begin
      memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aMsg);
    end);
end;

end.
```

