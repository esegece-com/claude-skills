# TsgcLib_RCON - Example

Usage of `TsgcLib_RCON` extracted from the **50.Other/02.RCON** demo. See the full project for context.

API reference: [TsgcLib_RCON](../reference/api/TsgcLib_RCON.md)
Source demo: `50.Other/02.RCON` (file `FRCON.pas`)

```pascal
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

```

