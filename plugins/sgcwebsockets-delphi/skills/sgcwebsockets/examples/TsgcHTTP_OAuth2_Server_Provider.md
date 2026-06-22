# TsgcHTTP_OAuth2_Server_Provider - Example

Usage of `TsgcHTTP_OAuth2_Server_Provider` extracted from the **20.HTTP_Protocol/08.OAuth2_ServerProvider** demo. See the full project for context.

API reference: [TsgcHTTP_OAuth2_Server_Provider](../reference/api/TsgcHTTP_OAuth2_Server_Provider.md)
Source demo: `20.HTTP_Protocol/08.OAuth2_ServerProvider` (file `FOAuth2_Server.pas`)

```pascal
procedure TFRMOAuth2Server.DoLog(const Text: string);
  begin
  TThread.Queue(nil,
  procedure
  begin
  if Assigned(memoLog) then
  memoLog.Lines.Add(Text);
  end);
  end;
  
  procedure TFRMOAuth2Server.DoOpenBrowser(const aEndpoint: string);
  begin
  {$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar('chrome'),
  PWideChar('https://' + txtHost.Text + ':' + txtDefaultPort.Text + aEndpoint), '', 0);
  {$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar('chrome'),
  PAnsiChar('https://' + txtHost.Text + ':' + txtDefaultPort.Text + aEndpoint), '', 0);
  {$ENDIF}
  end;
  
  procedure TFRMOAuth2Server.DoStart;
  begin
  if txtTenant.Text = '' then
  raise Exception.Create('Set the Tenant First!!!');
  if txtClientId.Text = '' then
  raise Exception.Create('Set the Client ID First!!!');
  if txtClientSecret.Text = '' then
  raise Exception.Create('Set the Client Secret First!!!');
  
  // ... oauth2 Azure AD
  WSServer.Authentication.Enabled := True;
  OAuth2Provider.ClearProviders;
  OAuth2Provider.RegisterProvider(
  'azure',
  txtClientId.Text,
  txtClientSecret.Text,
  Format('https://login.microsoftonline.com/%s/oauth2/v2.0/authorize', [txtTenant.Text]),
  Format('https://login.microsoftonline.com/%s/oauth2/v2.0/token', [txtTenant.Text]),
  txtScope.Text,
  txtURL.Text,
  txtCallbackURL.Text
  );
  
  // ... start server
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  WSServer.SSLOptions.Port := StrToInt(txtDefaultPort.Text);
  WSServer.SSLOptions.CertFile := 'sgc.pem';
  WSServer.SSLOptions.KeyFile := 'sgc.pem';
  WSServer.SSLOptions.RootCertFile := 'sgc.pem';
  WSServer.SSL := True;
  WSServer.Active := True;
  end;
  
  procedure TFRMOAuth2Server.DoStop;
  begin
  WSServer.Active := False;
  end;
  
  procedure TFRMOAuth2Server.OAuth2ProviderOAuth2IsPrivateEndpoint(Sender:
```

