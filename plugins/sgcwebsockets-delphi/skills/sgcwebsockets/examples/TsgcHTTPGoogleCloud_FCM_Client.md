# TsgcHTTPGoogleCloud_FCM_Client - Example

Usage of `TsgcHTTPGoogleCloud_FCM_Client` extracted from the **20.HTTP_Protocol/03.Google/03.Google_FCM** demo. See the full project for context.

API reference: [TsgcHTTPGoogleCloud_FCM_Client](../reference/api/TsgcHTTPGoogleCloud_FCM_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/03.Google_FCM` (file `FGoogleFCM.pas`)

```pascal
procedure TFRMGoogleFCM.btnLoadJSONSettingsClick(Sender: TObject);
  var
  oDialog: TOpenDialog;
  begin
  oDialog := TOpenDialog.Create(nil);
  Try
  oDialog.Filter := 'JSON Files|*.json';
  if oDialog.Execute then
  begin
  GoogleFCM.LoadSettingsFromFile(oDialog.FileName);
  
  txtProject.Text := GoogleFCM.GoogleCloudOptions.JWT.ProjectId;
  txtJWTClientEmail.Text := GoogleFCM.GoogleCloudOptions.JWT.ClientEmail;
  txtJWTPrivateKeyId.Text := GoogleFCM.GoogleCloudOptions.JWT.PrivateKeyId;
  memoJWTPrivateKey.Lines.Text := GoogleFCM.GoogleCloudOptions.JWT.PrivateKey.Text;
  end;
  Finally
  oDialog.Free;
  End;

procedure TFRMGoogleFCM.btnSendMessageClick(Sender: TObject);
  begin
  DoAuthenticate;
  
  DoLog('SendMessage', GoogleFCM.SendMessage(txtProject.text, memoPayload.lines.text));
  end;

GoogleFCM.GoogleCloudOptions.Authentication := gcaOAuth2;
GoogleFCM.GoogleCloudOptions.Authentication := gcaJWT;
procedure TFRMGoogleFCM.memoJWTPrivateKeyChange(Sender: TObject);
  begin
  GoogleFCM.GoogleCloudOptions.JWT.PrivateKey.Text := memoJWTPrivateKey.Lines.Text;
  end;

procedure TFRMGoogleFCM.txtClientIdChange(Sender: TObject);
  begin
  GoogleFCM.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
  end;

procedure TFRMGoogleFCM.txtClientSecretChange(Sender: TObject);
  begin
  GoogleFCM.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;
  end;

procedure TFRMGoogleFCM.txtJWTClientEmailChange(Sender: TObject);
  begin
  GoogleFCM.GoogleCloudOptions.JWT.ClientEmail := txtJWTClientEmail.Text;
  GoogleFCM.GoogleCloudOptions.JWT.Subject := txtJWTClientEmail.Text;
  end;

procedure TFRMGoogleFCM.txtJWTPrivateKeyIdChange(Sender: TObject);
  begin
  GoogleFCM.GoogleCloudOptions.JWT.PrivateKeyId := txtJWTPrivateKeyId.Text;
  end;

```

