# TsgcSTUNClient - Example

Full source of `FSTUNClient.pas` from the **35.P2P/02.STUN** demo, which uses `TsgcSTUNClient`.

API reference: [TsgcSTUNClient](../reference/api/TsgcSTUNClient.md)
Source demo: `35.P2P/02.STUN` (file `FSTUNClient.pas`)

```pascal
unit FSTUNClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcP2P_STUN_Classes, sgcP2P_STUN_Client, sgcP2P,
  sgcP2P_STUN_Types, sgcSocket_Classes;

type
  TFRMSTUNClient = class(TForm)
    stun_client: TsgcSTUNClient;
    pnlServerOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    memoLog: TMemo;
    cboTransport: TComboBox;
    Label1: TLabel;
    chkRetransmissions: TCheckBox;
    Label2: TLabel;
    txtRTO: TEdit;
    txtMaxRetries: TEdit;
    Label6: TLabel;
    Label7: TLabel;
    Label8: TLabel;
    chkLongTermCredentials: TCheckBox;
    txtUsername: TEdit;
    Label9: TLabel;
    txtPassword: TEdit;
    Label10: TLabel;
    pnlBottom: TPanel;
    btnRequestBinding: TButton;
    procedure btnRequestBindingClick(Sender: TObject);
    procedure stun_clientSTUNException(Sender: TObject; E: Exception);
    procedure stun_clientSTUNResponseError(Sender: TObject; const aSocket:
        TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aError:
        TsgcSTUN_ResponseError);
    procedure stun_clientSTUNResponseSuccess(Sender: TObject; const aSocket:
        TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aBinding:
        TsgcSTUN_ResponseBinding);
  private
    procedure DoLog(const aText: String);
  end;

var
  FRMSTUNClient: TFRMSTUNClient;

implementation

{$R *.dfm}

procedure TFRMSTUNClient.btnRequestBindingClick(Sender: TObject);
begin
  // stun server
  stun_client.Host := txtHost.Text;
  stun_client.Port := StrToInt(txtPort.Text);
  case cboTransport.ItemIndex of
    0:
      stun_client.Transport := stunUDP;
    1:
      stun_client.Transport := stunTCP;
  end;
  // retransmissions
  stun_client.RetransmissionOptions.Enabled := chkRetransmissions.Checked;
  stun_client.RetransmissionOptions.RTO := StrToInt(txtRTO.Text);
  stun_client.RetransmissionOptions.MaxRetries := StrToInt(txtMaxRetries.Text);
  // authentication
  if chkLongTermCredentials.Checked then
  begin
    stun_client.STUNOptions.Authentication.Credentials := stauLongTermCredential;
    stun_client.STUNOptions.Fingerprint := True;
  end
  else
  begin
    stun_client.STUNOptions.Authentication.Credentials := stauNone;
    stun_client.STUNOptions.Fingerprint := False;
  end;
  stun_client.STUNOptions.Authentication.Username := txtUsername.Text;
  stun_client.STUNOptions.Authentication.Password := txtPassword.Text;
  // send request binding
  stun_client.SendRequest;
  DoLog('*** ' + txtHost.Text + ':' + txtPort.Text + '***');
end;

procedure TFRMSTUNClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMSTUNClient.stun_clientSTUNException(Sender: TObject;
  E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMSTUNClient.stun_clientSTUNResponseError(Sender: TObject; const
    aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const
    aError: TsgcSTUN_ResponseError);
begin
  DoLog('#error: ' + IntToStr(aError.Code) + ' ' + aError.Reason);
end;

procedure TFRMSTUNClient.stun_clientSTUNResponseSuccess(Sender: TObject; const
    aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const
    aBinding: TsgcSTUN_ResponseBinding);
var
  i: Integer;
begin
  DoLog('#binding: ' + aBinding.RemoteIP + ':' + IntToStr(aBinding.RemotePort));

  for i := 0 to aMessage.Attributes.Count - 1 do
  begin
    case TsgcSTUN_Attribute(aMessage.Attributes.Items[i]).AttributeType of
      stmaFingerprint:
        DoLog('#fingerprint: ' + IntToStr(TsgcSTUN_Attribute_FINGERPRINT
          (aMessage.Attributes.Items[i]).Fingerprint));
      stmaSoftware:
        DoLog('#software: ' + TsgcSTUN_Attribute_SOFTWARE
          (aMessage.Attributes.Items[i]).Software);
      stmaResponse_Origin:
        DoLog('#response_origin: ' + TsgcSTUN_Attribute_RESPONSE_ORIGIN
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_RESPONSE_ORIGIN(aMessage.Attributes.Items
          [i]).Port));
      stmaOther_Address:
        DoLog('#other_address: ' + TsgcSTUN_Attribute_OTHER_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_OTHER_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
      stmaSource_Address:
        DoLog('#source_address: ' + TsgcSTUN_Attribute_SOURCE_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_SOURCE_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
      stmaChanged_Address:
        DoLog('#changed_address: ' + TsgcSTUN_Attribute_CHANGED_ADDRESS
          (aMessage.Attributes.Items[i]).Address + ':' +
          IntToStr(TsgcSTUN_Attribute_CHANGED_ADDRESS(aMessage.Attributes.Items
          [i]).Port));
    end;
  end;

  DoLog('');
end;

end.
```

