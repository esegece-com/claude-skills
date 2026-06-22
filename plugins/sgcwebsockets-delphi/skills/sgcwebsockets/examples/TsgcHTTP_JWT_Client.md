# TsgcHTTP_JWT_Client - Example

Usage of `TsgcHTTP_JWT_Client` extracted from the **20.HTTP_Protocol/05.JWT** demo. See the full project for context.

API reference: [TsgcHTTP_JWT_Client](../reference/api/TsgcHTTP_JWT_Client.md)
Source demo: `20.HTTP_Protocol/05.JWT` (file `FJWT_Client.pas`)

```pascal
procedure TFRMJWT_Client.btnOpenWebSocketClick(Sender: TObject);
  begin
  WSClient.Host := '127.0.0.1';
  WSClient.Port := 5430;
  
  JWTClient.JWTOptions.Header.alg := TsgcHTTP_JWT_Algorithm(cboAlgorithm.ItemIndex + 1);
  JWTClient.JWTOptions.Payload.iss := txtIssuer.Text;
  JWTClient.JWTOptions.Payload.iat := StrToInt(GetDateTimeUnix(Now, False));
  JWTClient.JWTOptions.Payload.nbf := StrToInt(GetDateTimeUnix(dateValidFrom.Date + timeValidFrom.Time, False));
  JWTClient.JWTOptions.Payload.exp := StrToInt(GetDateTimeUnix(dateExpiration.Date + timeExpiration.Time, False));
  
  WSClient.Authentication.Enabled := True;
  WSClient.Authentication.URL.Enabled := False;
  WSClient.Authentication.Token.Enabled := True;
  WSClient.Authentication.Token.JWT := JWTClient;
  
  WSClient.Active := True;
  end;

```

