# TsgcTDLib_Telegram - Example

Usage of `TsgcTDLib_Telegram` extracted from the **50.Other/01.Telegram_Client** demo. See the full project for context.

API reference: [TsgcTDLib_Telegram](../reference/api/TsgcTDLib_Telegram.md)
Source demo: `50.Other/01.Telegram_Client` (file `FSGCTelegram.pas`)

```pascal
procedure TFRMSGCTelegram.AddChatMember1Click(Sender: TObject);
  begin
  sgcTelegram.AddChatMember(InputBox('AddChatMember', 'Chat Id', FChatId),
  StrToInt(InputBox('AddChatMember', 'User Id', '0')));
  end;

procedure TFRMSGCTelegram.btnSendMessageClick(Sender: TObject);
  begin
  if txtMessage.Text <> '' then
  begin
  sgcTelegram.SendRichTextMessage(GetChatId, txtMessage.Text);
  txtMessage.Text := '';
  end;
  end;

procedure TFRMSGCTelegram.btnStartClick(Sender: TObject);
  begin
  sgcTelegram.Telegram.API.ApiHash := txtApiHash.Text;
  sgcTelegram.Telegram.API.ApiId := txtApiId.Text;
  sgcTelegram.Telegram.PhoneNumber := '';
  sgcTelegram.Telegram.BotToken := '';
  if chkLoginBot.Checked then
  sgcTelegram.Telegram.BotToken := txtBotToken.Text
  else
  sgcTelegram.Telegram.PhoneNumber := txtPhoneNumber.Text;
  
  sgcTelegram.Active := True;
  end;

procedure TFRMSGCTelegram.btnStopClick(Sender: TObject);
  begin
  DoStatus('');
  DoLog('');
  listChats.Clear;
  Chats.Clear;
  sgcTelegram.Active := False;
  end;

procedure TFRMSGCTelegram.BasicGroupsCreate1Click(Sender: TObject);
  begin
  sgcTelegram.CreateNewBasicGroupChat
  ([StrToInt(InputBox('User Id', 'First User Id', '0')),
  StrToInt(InputBox('User Id', 'Second User Id', '0'))],
  InputBox('Basic Group', 'Title Group', 'Basic Group Telegram'));
  end;

procedure TFRMSGCTelegram.btnSendFileClick(Sender: TObject);
  var
  oDialog: TOpenDialog;
  begin
  oDialog := TOpenDialog.Create(nil);
  Try
  if oDialog.Execute then
  sgcTelegram.SendDocumentMessage(GetChatId, oDialog.FileName);
  Finally
  oDialog.Free;
  End;

procedure TFRMSGCTelegram.Disable1Click(Sender: TObject);
  begin
```

