# TsgcHTTP_OAuth2_Server - Example

Usage of `TsgcHTTP_OAuth2_Server` extracted from the **20.HTTP_Protocol/02.OAuth2_Authentication** demo. See the full project for context.

API reference: [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md)
Source demo: `20.HTTP_Protocol/02.OAuth2_Authentication` (file `FOAuth2_Server.pas`)

```pascal
WSServer.Authentication.OAuth.OAuth2 := nil;
WSServer.Authentication.Enabled := chkOAuth2.Checked;
WSServer.Authentication.OAuth.OAuth2 := OAuth2;
```

