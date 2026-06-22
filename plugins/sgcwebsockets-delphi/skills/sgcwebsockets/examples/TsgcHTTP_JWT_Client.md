# TsgcHTTP_JWT_Client - Example

Full source of `FJWT_Client.pas` from the **20.HTTP_Protocol/05.JWT** demo, which uses `TsgcHTTP_JWT_Client`.

API reference: [TsgcHTTP_JWT_Client](../reference/api/TsgcHTTP_JWT_Client.md)
Source demo: `20.HTTP_Protocol/05.JWT` (file `FJWT_Client.pas`)

```pascal
unit FJWT_Client;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ComCtrls, StdCtrls, ExtCtrls, DateUtils, sgcHTTP_Classes,
  sgcHTTP_JWT_Client, sgcHTTP, sgcBase_Classes, sgcSocket_Classes,
  sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Client, sgcWebSocket, sgcHTTP_JWT_Types;

type
  TFRMJWT_Client = class(TForm)
    Button1: TButton;
    pnlTop: TPanel;
    txtIssuer: TEdit;
    Label1: TLabel;
    cboAlgorithm: TComboBox;
    Label2: TLabel;
    dateExpiration: TDateTimePicker;
    timeExpiration: TDateTimePicker;
    Label3: TLabel;
    Label4: TLabel;
    dateValidFrom: TDateTimePicker;
    timeValidFrom: TDateTimePicker;
    btnOpenWebSocket: TButton;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    JWTClient: TsgcHTTP_JWT_Client;
    btnCloseWebSocket: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnOpenWebSocketClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnCloseWebSocketClick(Sender: TObject);
  private
    procedure DoLog(const aText: string);
  public
    { Public declarations }
  end;

var
  FRMJWT_Client: TFRMJWT_Client;

implementation

{$R *.dfm}

uses
  sgcBase_Helpers;

procedure TFRMJWT_Client.btnCloseWebSocketClick(Sender: TObject);
begin
  WSClient.Active := False;
end;

procedure TFRMJWT_Client.btnOpenWebSocketClick(Sender: TObject);
begin
  WSClient.Host := '127.0.0.1';
  WSClient.Port := 5430;

  JWTClient.JWTOptions.Header.alg := TsgcHTTP_JWT_Algorithm(cboAlgorithm.ItemIndex + 1);
  JWTClient.JWTOptions.Payload.iss := txtIssuer.Text;
  JWTClient.JWTOptions.Payload.iat := StrToInt(GetDateTimeUnix(Now, False));
  JWTClient.JWTOptions.Payload.nbf := StrToInt(GetDateTimeUnix(dateValidFrom.Date + timeValidFrom.Time, False));
  JWTClient.JWTOptions.Payload.exp := StrToInt(GetDateTimeUnix(dateExpiration.Date + timeExpiration.Time, False));

  WSClient.Authentication.Enabled := True;
  WSClient.Authentication.URL.Enabled := False;
  WSClient.Authentication.Token.Enabled := True;
  WSClient.Authentication.Token.JWT := JWTClient;

  WSClient.Active := True;
end;

procedure TFRMJWT_Client.FormCreate(Sender: TObject);
begin
  dateValidFrom.Date := Trunc(now);
  timeValidFrom.Time := Frac(now);

  dateExpiration.Date := Trunc(Now);
  TimeExpiration.Time := IncMinute(Frac(Now), 10);
end;

procedure TFRMJWT_Client.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMJWT_Client.WSClientConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TFRMJWT_Client.WSClientDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TFRMJWT_Client.WSClientException(Connection: TsgcWSConnection;
  E: Exception);
begin
  DoLog('#exception: ' + E.message);
end;

procedure TFRMJWT_Client.WSClientMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog(Text);
  Connection.Disconnect;
end;

end.
```

