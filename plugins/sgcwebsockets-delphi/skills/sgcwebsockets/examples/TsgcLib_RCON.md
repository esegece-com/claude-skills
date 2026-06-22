# TsgcLib_RCON - Example

Full source of `FRCON.pas` from the **50.Other/02.RCON** demo, which uses `TsgcLib_RCON`.

API reference: [TsgcLib_RCON](../reference/api/TsgcLib_RCON.md)
Source demo: `50.Other/02.RCON` (file `FRCON.pas`)

```pascal
unit FRCON;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, sgcBase_Classes, sgcLib_RCON_Client,
  sgcLibs;

type
  TFRMRCON = class(TForm)
    RCON: TsgcLib_RCON;
    pnlTop: TPanel;
    pnlBody: TPanel;
    Memo1: TMemo;
    txtHost: TEdit;
    txtPort: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    btnConnect: TButton;
    btnDisconnect: TButton;
    Label3: TLabel;
    txtPassword: TEdit;
    btnExecCommand: TButton;
    txtCommand: TEdit;
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnExecCommandClick(Sender: TObject);
    procedure RCONAuthenticate(Sender: TObject; Authenticated: Boolean; const
        aPacket: TsgcRCON_Packet);
    procedure RCONConnect(Sender: TObject);
    procedure RCONDisconnect(Sender: TObject);
    procedure RCONException(Sender: TObject; E: Exception);
    procedure RCONResponse(Sender: TObject; const aResponse: string; const aPacket:
        TsgcRCON_Packet);
  private
    { Private declarations }
  public
    procedure DoLog(const aValue: string);
    { Public declarations }
  end;

var
  FRMRCON: TFRMRCON;

implementation

{$R *.dfm}

procedure TFRMRCON.btnConnectClick(Sender: TObject);
begin
  RCON.RCON_Options.Host := txtHost.text;
  RCON.RCON_Options.Port := StrToInt(txtPort.text);
  RCON.RCON_Options.Password := txtPassword.text;

  RCON.Active := True;
end;

procedure TFRMRCON.btnDisconnectClick(Sender: TObject);
begin
  RCON.Active := False;
end;

procedure TFRMRCON.btnExecCommandClick(Sender: TObject);
begin
  RCON.ExecCommand(txtCommand.Text);
end;

procedure TFRMRCON.DoLog(const aValue: string);
begin
  Memo1.lines.Add(aValue);
end;

procedure TFRMRCON.RCONAuthenticate(Sender: TObject; Authenticated: Boolean;
    const aPacket: TsgcRCON_Packet);
begin
  if Authenticated then
    DoLog('#authenticated')
  else
    DoLog('#not authenticated');
end;

procedure TFRMRCON.RCONConnect(Sender: TObject);
begin
  DoLog('#connected');
end;

procedure TFRMRCON.RCONDisconnect(Sender: TObject);
begin
  DoLog('#disconnected');
end;

procedure TFRMRCON.RCONException(Sender: TObject; E: Exception);
begin
  DoLog('#exception: ' + E.message);
end;

procedure TFRMRCON.RCONResponse(Sender: TObject; const aResponse: string; const
    aPacket: TsgcRCON_Packet);
begin
  DoLog(aResponse);
end;

end.
```

