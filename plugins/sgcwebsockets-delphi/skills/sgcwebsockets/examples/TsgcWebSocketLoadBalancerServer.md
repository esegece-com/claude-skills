# TsgcWebSocketLoadBalancerServer - Example

Usage of `TsgcWebSocketLoadBalancerServer` extracted from the **04.WebSocket_Other_Samples/03.LoadBalancer_Server** demo. See the full project for context.

API reference: [TsgcWebSocketLoadBalancerServer](../reference/api/TsgcWebSocketLoadBalancerServer.md)
Source demo: `04.WebSocket_Other_Samples/03.LoadBalancer_Server` (file `fLoadBalancer.pas`)

```pascal
procedure TfrmLoadBalancer.btnStartServersClick(Sender: TObject);
  begin
  LoadBalancer.HTTP2Options.Enabled := chkHTTP2.Checked;
  if LoadBalancer.HTTP2Options.Enabled then
  begin
  LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
  LoadBalancer.SSLOptions.Version := tls1_3;
  end
  else
  begin
  case cboOpenSSLAPI.ItemIndex of
  0: LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_0;
  1: LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
  2: LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  end;
  case cboTLSVersion.ItemIndex of
  0: LoadBalancer.SSLOptions.Version := tlsUndefined;
  1: LoadBalancer.SSLOptions.Version := tls1_0;
  2: LoadBalancer.SSLOptions.Version := tls1_1;
  3: LoadBalancer.SSLOptions.Version := tls1_2;
  4: LoadBalancer.SSLOptions.Version := tls1_3;
  end;

LoadBalancer.SSL := chkSSL.Checked;
Client1.TLSOptions.OpenSSL_Options.APIVersion := LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion;
Client1.LoadBalancer.TLS := LoadBalancer.SSL;
Client2.TLSOptions.OpenSSL_Options.APIVersion := LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion;
Client2.LoadBalancer.TLS := LoadBalancer.SSL;
Client3.TLSOptions.OpenSSL_Options.APIVersion := LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion;
Client3.LoadBalancer.TLS := LoadBalancer.SSL;
Client4.TLSOptions.OpenSSL_Options.APIVersion := LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion;
Client4.LoadBalancer.TLS := LoadBalancer.SSL;
Client5.TLSOptions.OpenSSL_Options.APIVersion := LoadBalancer.SSLOptions.OpenSSL_Options.APIVersion;
Client5.LoadBalancer.TLS := LoadBalancer.SSL;
LoadBalancer.Active := True;
procedure TfrmLoadBalancer.btnStopServersClick(Sender: TObject);
  begin
  LoadBalancer.Active := False;
  
  Server1.Active := False;
  Server2.Active := False;
  Server3.Active := False;
  end;

```

