# TIdIcmpClient - Example

Full source of `fPingClient.pas` from the **PingClient** demo, which uses `TIdIcmpClient`.

API reference: [TIdIcmpClient](../reference/api/TIdIcmpClient.md)
Source demo: `PingClient` (file `fPingClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy Ping Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fPingClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdRawBase, IdRawClient, IdIcmpClient;

type
  TfrmPingClient = class(TForm)
    lblHost: TLabel;
    lblCount: TLabel;
    txtHost: TEdit;
    txtCount: TEdit;
    btnPing: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnPingClick(Sender: TObject);
  private
    FIcmpClient: TIdIcmpClient;
    procedure DoLog(const aMessage: String);
    procedure OnIcmpReply(ASender: TComponent;
      const AReplyStatus: TReplyStatus);
  public
  end;

var
  frmPingClient: TfrmPingClient;

implementation

{$R *.dfm}

procedure TfrmPingClient.FormCreate(Sender: TObject);
begin
  FIcmpClient := TIdIcmpClient.Create(nil);
  FIcmpClient.OnReply := OnIcmpReply;
end;

procedure TfrmPingClient.FormDestroy(Sender: TObject);
begin
  FIcmpClient.Free;
end;

procedure TfrmPingClient.btnPingClick(Sender: TObject);
var
  i, vCount: Integer;
  vSent, vReceived: Integer;
  vMinTime, vMaxTime, vTotalTime: Integer;
begin
  memoLog.Clear;
  vCount := StrToIntDef(txtCount.Text, 4);
  FIcmpClient.Host := txtHost.Text;
  FIcmpClient.ReceiveTimeout := 3000;

  DoLog('Pinging ' + FIcmpClient.Host + '...');
  DoLog('');

  vSent := 0;
  vReceived := 0;
  vMinTime := MaxInt;
  vMaxTime := 0;
  vTotalTime := 0;

  try
    for i := 1 to vCount do
    begin
      vSent := vSent + 1;
      FIcmpClient.Ping;
      Application.ProcessMessages;

      if FIcmpClient.ReplyStatus.ReplyStatusType = rsEcho then
      begin
        DoLog('Reply from ' + FIcmpClient.ReplyStatus.FromIpAddress + ': bytes='
          + IntToStr(FIcmpClient.ReplyStatus.BytesReceived) + ' time=' +
          IntToStr(FIcmpClient.ReplyStatus.MsRoundTripTime) + 'ms TTL=' +
          IntToStr(FIcmpClient.ReplyStatus.TimeToLive));
        vReceived := vReceived + 1;
        if FIcmpClient.ReplyStatus.MsRoundTripTime < vMinTime then
          vMinTime := FIcmpClient.ReplyStatus.MsRoundTripTime;
        if FIcmpClient.ReplyStatus.MsRoundTripTime > vMaxTime then
          vMaxTime := FIcmpClient.ReplyStatus.MsRoundTripTime;
        vTotalTime := vTotalTime + FIcmpClient.ReplyStatus.MsRoundTripTime;
      end
      else
        DoLog('Request timed out.');

      if i < vCount then
        Sleep(1000);

      Application.ProcessMessages;
    end;

    DoLog('');
    DoLog('Ping statistics for ' + FIcmpClient.Host + ':');
    DoLog('    Packets: Sent = ' + IntToStr(vSent) + ', Received = ' +
      IntToStr(vReceived) + ', Lost = ' + IntToStr(vSent - vReceived));
    if vReceived > 0 then
    begin
      DoLog('Approximate round trip times:');
      DoLog('    Minimum = ' + IntToStr(vMinTime) + 'ms, Maximum = ' +
        IntToStr(vMaxTime) + 'ms, Average = ' +
        IntToStr(vTotalTime div vReceived) + 'ms');
    end;
  except
    on E: Exception do
      DoLog('Error: ' + E.Message);
  end;
end;

procedure TfrmPingClient.DoLog(const aMessage: String);
begin
  memoLog.Lines.Add(aMessage);
end;

procedure TfrmPingClient.OnIcmpReply(ASender: TComponent;
  const AReplyStatus: TReplyStatus);
begin
  // Reply handled in btnPingClick
end;

end.
```

