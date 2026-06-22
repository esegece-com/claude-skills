# TsgcTURNServer - Example

Full source of `FTURNServer.pas` from the **35.P2P/03.TURN** demo, which uses `TsgcTURNServer`.

API reference: [TsgcTURNServer](../reference/api/TsgcTURNServer.md)
Source demo: `35.P2P/03.TURN` (file `FTURNServer.pas`)

```pascal
unit FTURNServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcP2P, sgcWebSocket_Types,
  sgcP2P_STUN_Classes, sgcP2P_TURN_Server, sgcSocket_Classes,
  sgcP2P_STUN_Server, sgcP2P_TURN_Classes;

type
  TFRMTURNServer = class(TForm)
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
    turn_server: TsgcTURNServer;
    Label4: TLabel;
    Label5: TLabel;
    Label7: TLabel;
    txtRealm: TEdit;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure turn_serverSTUNException(Sender: TObject; E: Exception);
    procedure turn_serverSTUNRequestAuthorization(Sender: TObject;
      const aRequest: TsgcSTUN_Message; const aUsername, aRealm: string;
      var Password: string);
    procedure turn_serverTURNCreateAllocation(Sender: TObject; const aSocket:
        TsgcSocketConnection; const Allocation: TsgcTURNAllocationItem);
  private
    procedure DoLog(const aText: String);
    procedure OnMessageEvent(Sender: TObject; const aValue: string);
  end;

var
  FRMTURNServer: TFRMTURNServer;

implementation

uses
  sgcBase_Sync;

{$R *.dfm}

procedure TFRMTURNServer.FormCreate(Sender: TObject);
begin
  sgcSyncMessages.OnMessage := OnMessageEvent;

  btnStart.Click;
end;

procedure TFRMTURNServer.btnStartClick(Sender: TObject);
begin
  if turn_server.Active then
    turn_server.Active := False;

  // only for update memo, production let the value neNoSync
  turn_server.NotifyEvents := neAsynchronous;

  // initialize server
  turn_server.Host := txtHost.Text;
  turn_server.Port := StrToInt(txtPort.Text);
  // bindings
  turn_server.Bindings.Clear;
  With turn_server.Bindings.Add do
  begin
    IP := txtHost.Text;
    Port := StrToInt(txtPort.Text);
  end;
  // stun options
  turn_server.STUNOptions.Authentication.Enabled := False;

  // turn options
  turn_server.TURNOptions.Authentication.Enabled :=
    chkLongTermCredentials.Checked;
  turn_server.TURNOptions.Authentication.LongTermCredentials.Enabled :=
    chkLongTermCredentials.Checked;
  turn_server.TURNOptions.Authentication.LongTermCredentials.Realm :=
    txtRealm.Text;

  turn_server.Active := True;

  DoLog('#start server');
end;

procedure TFRMTURNServer.btnStopClick(Sender: TObject);
begin
  turn_server.Active := False;

  DoLog('#stop server');
end;

procedure TFRMTURNServer.DoLog(const aText: String);
begin
  sgcSyncMessages.Queue(aText);
end;

procedure TFRMTURNServer.OnMessageEvent(Sender: TObject; const aValue: string);
begin
  memoLog.Lines.Add(aValue);
end;

procedure TFRMTURNServer.turn_serverSTUNException(Sender: TObject;
  E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMTURNServer.turn_serverSTUNRequestAuthorization(Sender: TObject;
  const aRequest: TsgcSTUN_Message; const aUsername, aRealm: string;
  var Password: string);
begin
  if (aUsername = txtUsername.Text) and
    (aRealm = turn_server.TURNOptions.Authentication.LongTermCredentials.Realm)
  then
    Password := txtPassword.Text;
end;

procedure TFRMTURNServer.turn_serverTURNCreateAllocation(Sender: TObject; const
    aSocket: TsgcSocketConnection; const Allocation: TsgcTURNAllocationItem);
begin
  DoLog('New Allocation: ' + Allocation.RelayIP + ':' +
    IntToStr(Allocation.RelayPort));
end;

end.
```

