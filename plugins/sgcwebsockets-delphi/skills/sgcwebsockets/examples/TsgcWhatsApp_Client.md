# TsgcWhatsApp_Client - Example

Usage of `TsgcWhatsApp_Client` extracted from the **50.Other/05.WhatsApp** demo. See the full project for context.

API reference: [TsgcWhatsApp_Client](../reference/api/TsgcWhatsApp_Client.md)
Source demo: `50.Other/05.WhatsApp` (file `FWhatsApp.pas`)

```pascal
procedure TFRMWhatsApp.FormCreate(Sender: TObject);
  begin
  DoLoadSettings;
  
  // ... using neAsynchronous to update the memo control
  // ... in production set the value neNoSync
  whatsapp.NotifyEvents := neAsynchronous;
  end;

procedure TFRMWhatsApp.btnSendMessageClick(Sender: TObject);
  begin
  whatsapp.WhatsappOptions.PhoneNumberId := txtPhoneNumberId.Text;
  whatsapp.WhatsappOptions.Token := txtToken.Text;
  
  DoLog('Message Sent: ' + whatsapp.SendMessageLocation(txtMessagePhone.Text,
  '10', '2', 'My Address', 'C/ La Pau 79 Manresa'));
  
  txtMessageText.Text := '';
  end;

procedure TFRMWhatsApp.btnStartServerClick(Sender: TObject);
  begin
  whatsapp.ServerOptions.IP := txtServerIP.Text;
  whatsapp.ServerOptions.Port := StrToInt(txtServerPort.Text);
  whatsapp.ServerOptions.SSL := chkServerSSL.Checked;
  if whatsapp.ServerOptions.SSL then
  begin
  whatsapp.ServerOptions.SSLOptions.CertFile := txtServerCertificate.Text;
  whatsapp.ServerOptions.SSLOptions.KeyFile := txtServerKeyFile.Text;
  whatsapp.ServerOptions.SSLOptions.Port := StrToInt(txtServerPort.Text);
  end;
  whatsapp.ServerOptions.WebhookOptions.Endpoint :=
  txtServerWebhookEndpoint.Text;
  whatsapp.ServerOptions.WebhookOptions.Token := txtServerWebhookToken.Text;
  
  whatsapp.WhatsappOptions.PhoneNumberId := txtPhoneNumberId.Text;
  whatsapp.WhatsappOptions.Token := txtToken.Text;
  
  whatsapp.StartServer;
  end;

procedure TFRMWhatsApp.btnStopServerClick(Sender: TObject);
  begin
  whatsapp.StopServer;
  end;

procedure TFRMWhatsApp.DoWhatsApp_ButtonReply(const aTo: string;
  const aButtonReply
  : TsgcWhatsApp_Receive_Message_Message_Interactive_ButtonReply);
  begin
  if aButtonReply.Id = 'Delphi' then
  whatsapp.SendMessageText(aTo,
  sgcDecodeJSON('\ud83d\udc4d\ud83d\udc4d\ud83d\udc4d'))
  else if aButtonReply.Id = 'C++' then
  whatsapp.SendMessageText(aTo,
  sgcDecodeJSON('\ud83d\udc4f\ud83d\udc4f\ud83d\udc4f'))
  else
  whatsapp.SendMessageText(aTo,
  sgcDecodeJSON('\ud83d\ude31\ud83d\ude31\ud83d\ude31'));
  end;
```

