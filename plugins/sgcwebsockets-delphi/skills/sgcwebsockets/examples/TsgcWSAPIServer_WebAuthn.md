# TsgcWSAPIServer_WebAuthn - Example

Usage of `TsgcWSAPIServer_WebAuthn` extracted from the **20.HTTP_Protocol/12.WebAuthn** demo. See the full project for context.

API reference: [TsgcWSAPIServer_WebAuthn](../reference/api/TsgcWSAPIServer_WebAuthn.md)
Source demo: `20.HTTP_Protocol/12.WebAuthn` (file `FWebAuthn_Server.pas`)

```pascal
procedure TFRMWebAuthnServer.btnStartClick(Sender: TObject);
  begin
  // ... enable for testing
  WebAuthnServer.EndpointsOptions.Test.Enabled := True;
  // ... WebAuthn options
  WebAuthnServer.WebAuthnOptions.RelyingParty := txtRelyingParty.text;
  // ... Fido Metadata Service
  WebAuthnServer.WebAuthnOptions.MDS.Enabled := True;
  WebAuthnServer.WebAuthnOptions.MDS.MDS_FileName := 'blob.jwt';
  WebAuthnServer.WebAuthnOptions.MDS.RootCert_FileName := 'root-r3.crt';
  WebAuthnServer.WebAuthnOptions.MDS.LeafCertificateCRL := True;
  
  // ... bindings
  Server.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  Server.Bindings.Clear;
  With Server.Bindings.Add do
  begin
  Port := StrToInt(txtDefaultPort.Text);
  IP := txtHost.Text;
  end;
  Server.SSL := True;
  
  // ... active
  Server.Active := True;
  end;

procedure TFRMWebAuthnServer.DoLog(const aText: String);
  begin
  TThread.Queue(nil,
  procedure
  begin
  if Assigned(memoLog) then
  memoLog.Lines.Add(aText);
  end);
  end;
  
  procedure TFRMWebAuthnServer.DoOpenBrowser(const aBrowserName: string);
  begin
  {$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
  PWideChar('https://' + txtRelyingParty.text + ':' + txtDefaultPort.Text +
  WebAuthnServer.EndpointsOptions.Test.Endpoint), '', 0);
  {$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
  PAnsiChar('https://' + txtRelyingParty.text + ':' + txtDefaultPort.Text +
  WebAuthnServer.EndpointsOptions.Test.Endpoint), '', 0);
  {$ENDIF}
  end;
  
  procedure TFRMWebAuthnServer.serverShutdown(Sender: TObject);
  begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;
  
  procedure TFRMWebAuthnServer.serverStartup(Sender: TObject);
  begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
  end;
```

