# TsgcWSPServer_Presence - Example

Usage of `TsgcWSPServer_Presence` extracted from the **02.WebSocket_Protocols/03.Presence_Protocol** demo. See the full project for context.

API reference: [TsgcWSPServer_Presence](../reference/api/TsgcWSPServer_Presence.md)
Source demo: `02.WebSocket_Protocols/03.Presence_Protocol` (file `FPresenceServer.pas`)

```pascal
procedure TForm16.btnStartClick(Sender: TObject);
  begin
  Presence.EncodeBase64 := chkBase64.Checked;
  Server.Port := StrToInt(txtPort.Text);
  Server.Active := True;
  end;

procedure TForm16.pagePresenceHTMLTag(Sender: TObject; Tag: TTag; const
  TagString: string; TagParams: TStrings; var ReplaceText: string);
  begin
  if TagString = 'port' then
  ReplaceText := txtPort.Text
  else if TagString = 'host' then
  ReplaceText := txtHost.Text
  else if TagString = 'b64' then
  begin
  if Presence.EncodeBase64 then
  ReplaceText := 'true'
  else
  ReplaceText := 'false';
  end;
  end;

procedure TForm16.ServerCommandGet(AContext: TIdContext; ARequestInfo:
  TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
  begin
  if ARequestInfo.Document = '/jquery.mobile.css' then
  begin
  AResponseInfo.ContentText := pageJQueryMobileCSS.Content;
  AResponseInfo.ContentType := 'text/css';
  AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.js' then
  begin
  AResponseInfo.ContentText := pageJQuery.Content;
  AResponseInfo.ContentType := 'text/javascript';
  AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.mobile.js' then
  begin
  AResponseInfo.ContentText := pageJQueryMobile.Content;
  AResponseInfo.ContentType := 'text/javascript';
  AResponseInfo.ResponseNo := 200;
  end
  else
  begin
  AResponseInfo.ContentText := pagePresence.Content;
  AResponseInfo.ContentType := 'text/html';
  AResponseInfo.ResponseNo := 200;
  end;
  end;

```

