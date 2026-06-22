# TsgcWSAPIServer_WebPush - Example

Usage of `TsgcWSAPIServer_WebPush` extracted from the **20.HTTP_Protocol/11.WebPush_Notifications** demo. See the full project for context.

API reference: [TsgcWSAPIServer_WebPush](../reference/api/TsgcWSAPIServer_WebPush.md)
Source demo: `20.HTTP_Protocol/11.WebPush_Notifications` (file `FWebPush_Server.pas`)

```pascal
procedure TFRMWebPushServer.btnBroadcastClick(Sender: TObject);
  var
  oMessage: TsgcWebPushMessage;
  begin
  oMessage := TsgcWebPushMessage.Create;
  Try
  oMessage.Title := 'eSeGeCe Notification';
  oMessage.Body := txtBody.Text;
  oMessage.Icon := 'https://www.esegece.com/images/esegece_logo_small.png';
  oMessage.Url := 'https://www.esegece.com';
  
  WebPushServer.BroadcastNotification(oMessage);
  Finally
  sgcFree(oMessage);
  End;

procedure TFRMWebPushServer.FormCreate(Sender: TObject);
  var
  i: Integer;
  oList: TStringList;
  oSubscription: TsgcHTTP_API_WebPush_PushSubscription;
  begin
  if FileExists('subscriptions.txt') then
  begin
  Subscriptions.LoadFromFile('subscriptions.txt');
  
  for i := 0 to Subscriptions.Count - 1 do
  begin
  oList := TStringList.Create;
  Try
  oList.Delimiter := Chr(9);
  oList.StrictDelimiter := True;
  oList.DelimitedText := Subscriptions[i];
  
  if oList.Count = 3 then
  begin
  oSubscription := TsgcHTTP_API_WebPush_PushSubscription.Create;
  Try
  oSubscription.Endpoint := oList[0];
  oSubscription.PublicKey := oList[1];
  oSubscription.AuthSecret := oList[2];
  
  WebPushServer.Subscriptions.AddSubscription(oSubscription)
  Finally
  sgcFree(oSubscription);
  End;
  end;
  Finally
  sgcFree(oList);
  End;
  end;

procedure TFRMWebPushServer.btnStartClick(Sender: TObject);
  begin
  // ... webpush config
  WebPushServer.WebPush.VAPID.PEM.PrivateKey.Text :=
  memoPEMPrivateKey.Lines.Text;
  WebPushServer.WebPush.VAPID.DER.PublicKey := txtDERPublicKey.Text;
  WebPushServer.WebPush.VAPID.DER.PrivateKey := txtDERPrivateKey.Text;
  
```

