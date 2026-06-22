# TsgcHTTP_JWT_Server - Example

Full source of `FJWT_Server.pas` from the **20.HTTP_Protocol/05.JWT** demo, which uses `TsgcHTTP_JWT_Server`.

API reference: [TsgcHTTP_JWT_Server](../reference/api/TsgcHTTP_JWT_Server.md)
Source demo: `20.HTTP_Protocol/05.JWT` (file `FJWT_Server.pas`)

```pascal
unit FJWT_Server;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils,
  // indy
  IdContext,
  // sgc
  sgcBase_Classes, sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_Types,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcIdCustomHTTPServer, sgcSocket_Classes, sgcHTTP_Classes, sgcHTTP_JWT_Server,
  sgcHTTP;

type
  TFRMJWTServer = class(TForm)
    server: TsgcWebSocketHTTPServer;
    btnStart: TButton;
    btnStop: TButton;
    Label1: TLabel;
    Label2: TLabel;
    txtHost: TEdit;
    Label3: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    pnlLeft: TPanel;
    pnlOptions: TPanel;
    memoLog: TMemo;
    JWTServer: TsgcHTTP_JWT_Server;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure JWTServerJWTAfterValidateToken(Sender: TObject; aConnection:
        TsgcWSConnection; aToken, aHeader, aPayload, aError: string; var Valid:
        Boolean);
    procedure JWTServerJWTException(Sender: TObject; aConnection: TsgcWSConnection;
        E: Exception);
    procedure serverCommandGet(AContext: TIdContext; ARequestInfo:
        TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure serverConnect(Connection: TsgcWSConnection);
    procedure serverShutdown(Sender: TObject);
    procedure serverStartup(Sender: TObject);
  private
    procedure DoLog(const aText: String);
  public
    { Public declarations }
  end;

var
  FRMJWTServer: TFRMJWTServer;

implementation

{$R *.dfm}

procedure TFRMJWTServer.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TFRMJWTServer.btnStartClick(Sender: TObject);
begin
  // ... bindings
  server.Port := StrToInt(txtDefaultPort.Text);
  server.Bindings.Clear;
  With server.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... active
  server.Active := True;
end;

procedure TFRMJWTServer.btnStopClick(Sender: TObject);
begin
  server.Active := False;
end;

procedure TFRMJWTServer.DoLog(const aText: String);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TFRMJWTServer.JWTServerJWTAfterValidateToken(Sender: TObject;
    aConnection: TsgcWSConnection; aToken, aHeader, aPayload, aError: string;
    var Valid: Boolean);
begin
  if Valid then
    DoLog('#Valid JWT: ' + aHeader + ' ' + aPayload)
  else
    DoLog('#Invalid JWT: ' + aError);
end;

procedure TFRMJWTServer.JWTServerJWTException(Sender: TObject; aConnection:
    TsgcWSConnection; E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMJWTServer.serverCommandGet(AContext: TIdContext; ARequestInfo:
    TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
begin
  AResponseInfo.ResponseNo := 200;
  AResponseInfo.ContentType := ARequestInfo.ContentType;
  AResponseInfo.ContentText := '<html><head><title>sgcWebSockets JWT Server</title></head><body>JWT Test Page.</body></html>';
end;

procedure TFRMJWTServer.serverConnect(Connection: TsgcWSConnection);
begin
  Connection.WriteData('JWT Token Successful');
end;

procedure TFRMJWTServer.serverShutdown(Sender: TObject);
begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMJWTServer.serverStartup(Sender: TObject);
begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

end.
```

