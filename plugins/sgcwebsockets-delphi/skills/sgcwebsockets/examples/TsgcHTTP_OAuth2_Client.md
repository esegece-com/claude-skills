# TsgcHTTP_OAuth2_Client - Example

Usage of `TsgcHTTP_OAuth2_Client` extracted from the **20.HTTP_Protocol/02.OAuth2_Authentication** demo. See the full project for context.

API reference: [TsgcHTTP_OAuth2_Client](../reference/api/TsgcHTTP_OAuth2_Client.md)
Source demo: `20.HTTP_Protocol/02.OAuth2_Authentication` (file `FOAuth2_Client.pas`)

```pascal
procedure TFRMOAuth2_Client.btnNewAuthorizationClick(Sender: TObject);
  begin
  OAuth2.AuthorizationServerOptions.AuthURL := txtAuthURL.Text;
  OAuth2.AuthorizationServerOptions.TokenURL := txtTokenURL.Text;
  OAuth2.AuthorizationServerOptions.Scope.Text := txtScope.Text;
  
  OAuth2.LocalServerOptions.IP := txtIP.Text;
  OAuth2.LocalServerOptions.RedirectURL := txtRedirectURL.Text;
  OAuth2.LocalServerOptions.Port := StrToInt(txtPort.Text);
  OAuth2.LocalServerOptions.SSL := chkSSL.Checked;
  if chkSSL.Checked then
  OAuth2.LocalServerOptions.SSLOptions.Port := StrToInt(txtPort.Text);
  
  OAuth2.OAuth2Options.ClientId := txtClientId.Text;
  OAuth2.OAuth2Options.ClientSecret := txtSecret.Text;
  OAuth2.OAuth2Options.Username := txtUsername.Text;
  OAuth2.OAuth2Options.Password := txtPassword.Text;
  
  // DPoP configuration
  OAuth2.DPoPOptions.Enabled := chkDPoP.Checked;
  if chkDPoP.Checked then
  begin
  OAuth2.DPoPOptions.Algorithm := dpopES256;
  // In a real app, load keys from secure storage
  // For demo purposes, the PrivateKey would be set by the user
  OAuth2.DPoPOptions.PrivateKey.LoadFromFile(txtPrivateKeyFile.Text);
  OAuth2.DPoPOptions.PublicKeyJWK := memoPublicKeyJWK.Lines.Text;
  
  if OAuth2.DPoPOptions.PrivateKey.Count = 0 then
  DoLog('DPoP: No private key configured. Set DPoPOptions.PrivateKey with an ES256 PEM key.');
  end;
  
  OAuth2.Stop;
  OAuth2.Start;
  end;

procedure TFRMOAuth2_Client.btnRefreshTokenClick(Sender: TObject);
  begin
  if txtRefreshToken.Text <> '' then
  OAuth2.Refresh(txtRefreshToken.Text);
  end;

OAuth2.OAuth2Options.GrantType := auth2Code;
OAuth2.OAuth2Options.GrantType := auth2Code;
OAuth2.OAuth2Options.GrantType := auth2ClientCredentials;
OAuth2.OAuth2Options.GrantType := auth2Code;
OAuth2.OAuth2Options.GrantType := auth2CodePKCE;
OAuth2.OAuth2Options.GrantType := auth2CodePKCE;
OAuth2.OAuth2Options.GrantType := auth2CodePKCE;
procedure TFRMOAuth2_Client.OAuth2AfterAccessToken(Sender: TObject;
  const Access_Token, Token_Type, Expires_In, Refresh_Token, Scope,
  RawParams: string; var Handled: Boolean);
  begin
  DoLog('After Access Token: ' + RawParams);
  
  txtAccessToken.Text := Access_Token;
  txtTokenType.Text := Token_Type;
  txtExpiresIn.Text := Expires_In;
  txtRefreshToken.Text := Refresh_Token;
  txtScopes.Text := Scope;
```

