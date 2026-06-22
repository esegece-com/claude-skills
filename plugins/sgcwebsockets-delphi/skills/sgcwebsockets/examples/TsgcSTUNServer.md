# TsgcSTUNServer - Example

Full source of `FSTUNServer.pas` from the **35.P2P/02.STUN** demo, which uses `TsgcSTUNServer`.

API reference: [TsgcSTUNServer](../reference/api/TsgcSTUNServer.md)
Source demo: `35.P2P/02.STUN` (file `FSTUNServer.pas`)

```pascal
unit FSTUNServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcP2P, sgcWebSocket_Types, sgcP2P_STUN_Classes,
  sgcP2P_STUN_Server;

type
  TFRMSTUNServer = class(TForm)
    pnlServerActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label6: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    chkLongTermCredentials: TCheckBox;
    txtUsername: TEdit;
    txtPassword: TEdit;
    memoLog: TMemo;
    stun_server: TsgcSTUNServer;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure stun_serverSTUNException(Sender: TObject; E: Exception);
    procedure stun_serverSTUNRequestAuthorization(Sender: TObject; const aRequest:
        TsgcSTUN_Message; const aUsername, aRealm: string; var Password: string);
  private
    procedure DoLog(const aText: String);
  end;

var
  FRMSTUNServer: TFRMSTUNServer;

implementation

{$R *.dfm}

procedure TFRMSTUNServer.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TFRMSTUNServer.btnStartClick(Sender: TObject);
begin
  if stun_server.Active then
    stun_server.Active := False;

  // only for update memo, production let the value neNoSync
  stun_server.NotifyEvents := neAsynchronous;

  // initialize server
  stun_server.Host := txtHost.Text;
  stun_server.Port := StrToInt(txtPort.Text);
  // bindings
  stun_server.Bindings.Clear;
  With stun_server.Bindings.Add do
  begin
    IP := txtHost.Text;
    Port := StrToInt(txtPort.Text);
  end;
  // long term credentials
  stun_server.STUNOptions.Authentication.Enabled := chkLongTermCredentials.Checked;
  stun_server.STUNOptions.Authentication.LongTermCredentials.Enabled := chkLongTermCredentials.Checked;

  stun_server.Active := True;

  DoLog('#start server');
end;

procedure TFRMSTUNServer.btnStopClick(Sender: TObject);
begin
  stun_server.Active := False;

  DoLog('#stop server');
end;

procedure TFRMSTUNServer.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMSTUNServer.stun_serverSTUNException(Sender: TObject; E:
    Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMSTUNServer.stun_serverSTUNRequestAuthorization(Sender: TObject;
    const aRequest: TsgcSTUN_Message; const aUsername, aRealm: string; var
    Password: string);
begin
  if aUsername = txtUsername.Text then
    Password := txtPassword.Text;
end;

end.
```

