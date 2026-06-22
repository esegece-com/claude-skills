# TsgcWSAPI_Discord - Example

Usage of `TsgcWSAPI_Discord` extracted from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo. See the full project for context.

API reference: [TsgcWSAPI_Discord](../reference/api/TsgcWSAPI_Discord.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
procedure TfrmWebSocketClient.btnDiscordGetUserClick(Sender: TObject);
  begin
  DoLog('#Discord GET: ' + DISCORD.GET_Request('/users/@me'));
  end;

procedure TfrmWebSocketClient.DISCORDDiscordDispatch(Sender: TObject;
  const aEvent, RawData: string);
  begin
  DoLog('#discord dispatch: ' + aEvent + ' ' + RawData);
  end;

procedure TfrmWebSocketClient.DISCORDDiscordReady(Sender: TObject;
  const RawData: string);
  begin
  DoLog('#discord Ready');
  end;

DISCORD.Client := nil;
DISCORD.DiscordOptions.BotOptions.BotName := txtDiscordBotName.Text;
DISCORD.DiscordOptions.BotOptions.BotURL := txtDiscordBotURL.Text;
DISCORD.DiscordOptions.BotOptions.Token := txtDiscordBotToken.Text;
DISCORD.Client := WSClient;
```

