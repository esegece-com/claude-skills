# TsgcTDLib_Telegram - Example

Full source of `FSGCTelegram.pas` from the **50.Other/01.Telegram_Client** demo, which uses `TsgcTDLib_Telegram`.

API reference: [TsgcTDLib_Telegram](../reference/api/TsgcTDLib_Telegram.md)
Source demo: `50.Other/01.Telegram_Client` (file `FSGCTelegram.pas`)

```pascal
unit FSGCTelegram;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, sgcBase_Classes, sgcLib_Telegram_Client,
  ExtCtrls, ComCtrls, Menus, sgcLibs;

type
  TFRMSGCTelegram = class(TForm)
    pnlConfiguration: TPanel;
    sgcTelegram: TsgcTDLib_Telegram;
    txtApiHash: TEdit;
    txtApiId: TEdit;
    txtPhoneNumber: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    btnStart: TButton;
    btnStop: TButton;
    pnlMessage: TPanel;
    txtMessage: TEdit;
    btnSendMessage: TButton;
    pnlBody: TPanel;
    PageControl1: TPageControl;
    tabMessages: TTabSheet;
    tabLog: TTabSheet;
    memoLog: TMemo;
    memoMessages: TMemo;
    StatusBar1: TStatusBar;
    listChats: TListBox;
    MainMenu1: TMainMenu;
    Menu: TMenuItem;
    Logout1: TMenuItem;
    Exit1: TMenuItem;
    BasicGroups1: TMenuItem;
    BasicGroupsCreate1: TMenuItem;
    SuperGroups1: TMenuItem;
    SuperGroupsCreate1: TMenuItem;
    SuperGroupDelete1: TMenuItem;
    Chats1: TMenuItem;
    GetChats1: TMenuItem;
    AddChatMember1: TMenuItem;
    JoinChatByInviteLink1: TMenuItem;
    Members1: TMenuItem;
    N1: TMenuItem;
    N3: TMenuItem;
    N4: TMenuItem;
    SecretChat1: TMenuItem;
    SecretChatCreate1: TMenuItem;
    PrivateChat1: TMenuItem;
    PrivateChatCreate1: TMenuItem;
    btnSendFile: TButton;
    Label4: TLabel;
    txtBotToken: TEdit;
    chkLoginBot: TCheckBox;
    Proxy1: TMenuItem;
    Add4: TMenuItem;
    HTTP1: TMenuItem;
    MTProto1: TMenuItem;
    Socks51: TMenuItem;
    Remove1: TMenuItem;
    Enable1: TMenuItem;
    Disable1: TMenuItem;
    GetProxies1: TMenuItem;
    N5: TMenuItem;
    N2: TMenuItem;
    GetChat1: TMenuItem;
    GetMembers1: TMenuItem;
    procedure FormDestroy(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure AddChatMember1Click(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure BasicGroupsCreate1Click(Sender: TObject);
    procedure btnSendFileClick(Sender: TObject);
    procedure chkLoginBotClick(Sender: TObject);
    procedure Disable1Click(Sender: TObject);
    procedure Enable1Click(Sender: TObject);
    procedure Exit1Click(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure GetChat1Click(Sender: TObject);
    procedure GetChats1Click(Sender: TObject);
    procedure GetMembers1Click(Sender: TObject);
    procedure GetProxies1Click(Sender: TObject);
    procedure HTTP1Click(Sender: TObject);
    procedure JoinChatByInviteLink1Click(Sender: TObject);
    procedure listChatsClick(Sender: TObject);
    procedure Logout1Click(Sender: TObject);
    procedure MTProto1Click(Sender: TObject);
    procedure PrivateChatCreate1Click(Sender: TObject);
    procedure Remove1Click(Sender: TObject);
    procedure SecretChatCreate1Click(Sender: TObject);
    procedure sgcTelegramBeforeReadEvent(Sender: TObject; const Text: string;
      var Handled: Boolean);
    procedure sgcTelegramConnectionStatus(Sender: TObject;
      const Status: string);
    procedure sgcTelegramAuthenticationCode(Sender: TObject; var Code: string);
    procedure sgcTelegramAuthenticationPassword(Sender: TObject;
      var Password: string);
    procedure sgcTelegramAuthorizationStatus(Sender: TObject;
      const Status: string);
    procedure sgcTelegramException(Sender: TObject; E: Exception);
    procedure sgcTelegramMessageDocument(Sender: TObject;
      MessageDocument: TsgcTelegramMessageDocument);
    procedure sgcTelegramMessagePhoto(Sender: TObject;
      MessagePhoto: TsgcTelegramMessagePhoto);
    procedure sgcTelegramMessageText(Sender: TObject;
      MessageText: TsgcTelegramMessageText);
    procedure sgcTelegramMessageVideo(Sender: TObject;
      MessageVideo: TsgcTelegramMessageVideo);
    procedure sgcTelegramNewChat(Sender: TObject; Chat: TsgcTelegramChat);
    procedure Socks51Click(Sender: TObject);
    procedure SuperGroupDelete1Click(Sender: TObject);
    procedure SuperGroupsCreate1Click(Sender: TObject);
    procedure txtMessageKeyPress(Sender: TObject; var Key: Char);
  private
    procedure DoLog(const aText: String);
    procedure DoStatus(const aStatus: String);
    procedure DoLogMessage(aChatId, aSenderUserId, aMessage: string);
  private
    FChatId: string;
    FChats: TStringList;
    function GetChats: TStringList;
    property Chats: TStringList read GetChats write FChats;
    function GetChatId: string;
  private
    procedure DoReadSettings;
    procedure DoSaveSettings;
  public
    { Public declarations }
  end;

var
  FRMSGCTelegram: TFRMSGCTelegram;

implementation

{$R *.dfm}

uses
  INIFiles;

procedure TFRMSGCTelegram.FormDestroy(Sender: TObject);
begin
  FreeAndNil(FChats);
end;

procedure TFRMSGCTelegram.FormCreate(Sender: TObject);
begin
  DoReadSettings;
end;

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
end;

procedure TFRMSGCTelegram.chkLoginBotClick(Sender: TObject);
begin
  txtPhoneNumber.Enabled := not chkLoginBot.Checked;
  txtBotToken.Enabled := chkLoginBot.Checked;
end;

procedure TFRMSGCTelegram.Disable1Click(Sender: TObject);
begin
  sgcTelegram.DisableProxy;
end;

procedure TFRMSGCTelegram.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
  StatusBar1.Panels[2].Text := aText;
end;

procedure TFRMSGCTelegram.DoLogMessage(aChatId, aSenderUserId,
  aMessage: string);
begin
  memoMessages.Lines.Add('Sender[' + aSenderUserId + '] ' + aMessage);
end;

procedure TFRMSGCTelegram.DoReadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtApiId.Text := oINI.ReadString('TELEGRAM', 'ApiId', '');
    txtApiHash.Text := oINI.ReadString('TELEGRAM', 'ApiHash', '');
    txtPhoneNumber.Text := oINI.ReadString('TELEGRAM', 'PhoneNumber', '');
    txtBotToken.Text := oINI.ReadString('TELEGRAM', 'BotToken', '');
    chkLoginBot.Checked := oINI.ReadBool('TELEGRAM', 'LoginBot', False);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMSGCTelegram.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('TELEGRAM', 'ApiId', txtApiId.Text);
    oINI.WriteString('TELEGRAM', 'ApiHash', txtApiHash.Text);
    oINI.WriteString('TELEGRAM', 'PhoneNumber', txtPhoneNumber.Text);
    oINI.WriteString('TELEGRAM', 'BotToken', txtBotToken.Text);
    oINI.WriteBool('TELEGRAM', 'LoginBot', chkLoginBot.Checked);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMSGCTelegram.DoStatus(const aStatus: String);
begin
  StatusBar1.Panels[0].Text := aStatus;
end;

procedure TFRMSGCTelegram.Enable1Click(Sender: TObject);
begin
  sgcTelegram.EnableProxy(StrToInt(InputBox('Enable',
    'Set Id Proxy to Enable', '')));
end;

procedure TFRMSGCTelegram.Exit1Click(Sender: TObject);
begin
  Close;
end;

procedure TFRMSGCTelegram.FormClose(Sender: TObject; var Action: TCloseAction);
begin
  DoSaveSettings;
end;

procedure TFRMSGCTelegram.GetChat1Click(Sender: TObject);
begin
  listChats.Clear;
  Chats.Clear;
  sgcTelegram.GetChat(GetChatId);
end;

function TFRMSGCTelegram.GetChatId: string;
begin
  while FChatId = '' do
    FChatId := InputBox('Set Chat Id', 'Chat Id', '0');
  result := FChatId;
end;

function TFRMSGCTelegram.GetChats: TStringList;
begin
  if not Assigned(FChats) then
    FChats := TStringList.Create;
  result := FChats;
end;

procedure TFRMSGCTelegram.GetChats1Click(Sender: TObject);
begin
  listChats.Clear;
  Chats.Clear;
  sgcTelegram.GetChats;
end;

procedure TFRMSGCTelegram.GetMembers1Click(Sender: TObject);
begin
  sgcTelegram.GetSupergroupMembers(StrToInt(InputBox('SuperGroup Id',
    'Set SuperGroup Id', '0')));
end;

procedure TFRMSGCTelegram.GetProxies1Click(Sender: TObject);
begin
  sgcTelegram.GetProxies;
end;

procedure TFRMSGCTelegram.HTTP1Click(Sender: TObject);
begin
  sgcTelegram.AddProxyHTTP(InputBox('Server', 'Set Server IP', ''),
    StrToInt(InputBox('Port', 'Set Server Port', '')),
    InputBox('Username', 'Set Username', ''),
    InputBox('Password', 'Set Password', ''), True);
end;

procedure TFRMSGCTelegram.JoinChatByInviteLink1Click(Sender: TObject);
begin
  sgcTelegram.JoinChatByInviteLink(InputBox('Join Chat By Invite Link',
    'Invite Link', ''));
end;

procedure TFRMSGCTelegram.listChatsClick(Sender: TObject);
var
  Selected: string;
begin
  Selected := listChats.Items[listChats.ItemIndex];
  if Selected <> '' then
  begin
    FChatId := Chats.Values[Selected];
    StatusBar1.Panels[1].Text := FChatId;
  end;
end;

procedure TFRMSGCTelegram.Logout1Click(Sender: TObject);
begin
  sgcTelegram.LogOut;
end;

procedure TFRMSGCTelegram.MTProto1Click(Sender: TObject);
begin
  sgcTelegram.AddProxyMTProto(InputBox('Server', 'Set Server IP', ''),
    StrToInt(InputBox('Port', 'Set Server Port', '')),
    InputBox('Secret', 'Set Secret', ''));
end;

procedure TFRMSGCTelegram.PrivateChatCreate1Click(Sender: TObject);
begin
  sgcTelegram.CreatePrivateChat(StrToInt(InputBox('New Private Chat',
    'User Id', '0')));
end;

procedure TFRMSGCTelegram.Remove1Click(Sender: TObject);
begin
  sgcTelegram.RemoveProxy(StrToInt(InputBox('Remove',
    'Set Id Proxy to Remove', '')));
end;

procedure TFRMSGCTelegram.SecretChatCreate1Click(Sender: TObject);
begin
  sgcTelegram.CreateNewSecretChat(StrToInt(InputBox('New Secret Chat',
    'User Id', '0')));
end;

procedure TFRMSGCTelegram.sgcTelegramAuthenticationCode(Sender: TObject;
  var Code: string);
begin
  Code := InputBox('Telegram', 'Introduce Telegram Code', '');
end;

procedure TFRMSGCTelegram.sgcTelegramAuthenticationPassword(Sender: TObject;
  var Password: string);
begin
  Password := InputBox('Telegram', 'Introduce Telegram Password', '');
end;

procedure TFRMSGCTelegram.sgcTelegramAuthorizationStatus(Sender: TObject;
  const Status: string);
begin
  if Status = 'authorizationStateReady' then
  begin
    if not chkLoginBot.Checked then
      sgcTelegram.GetChats;
  end;
end;

procedure TFRMSGCTelegram.sgcTelegramBeforeReadEvent(Sender: TObject;
  const Text: string; var Handled: Boolean);
begin
  DoLog(Text);
end;

procedure TFRMSGCTelegram.sgcTelegramConnectionStatus(Sender: TObject;
  const Status: string);
begin
  DoStatus(Status);
  if Status = 'connectionStateReady' then
  begin
    if not chkLoginBot.Checked then
      sgcTelegram.GetChats;
  end;
end;

procedure TFRMSGCTelegram.sgcTelegramException(Sender: TObject; E: Exception);
begin
  DoLog(E.Message);
end;

procedure TFRMSGCTelegram.sgcTelegramMessageDocument(Sender: TObject;
  MessageDocument: TsgcTelegramMessageDocument);
begin
  DoLogMessage(MessageDocument.ChatId, IntToStr(MessageDocument.SenderUserId),
    'New Document: ' + MessageDocument.FileName);
end;

procedure TFRMSGCTelegram.sgcTelegramMessagePhoto(Sender: TObject;
  MessagePhoto: TsgcTelegramMessagePhoto);
begin
  DoLogMessage(MessagePhoto.ChatId, IntToStr(MessagePhoto.SenderUserId),
    'New Photo: ' + MessagePhoto.PhotoId);
end;

procedure TFRMSGCTelegram.sgcTelegramMessageText(Sender: TObject;
  MessageText: TsgcTelegramMessageText);
begin
  DoLogMessage(MessageText.ChatId, IntToStr(MessageText.SenderUserId),
    MessageText.Text);
end;

procedure TFRMSGCTelegram.sgcTelegramMessageVideo(Sender: TObject;
  MessageVideo: TsgcTelegramMessageVideo);
begin
  DoLogMessage(MessageVideo.ChatId, IntToStr(MessageVideo.SenderUserId),
    MessageVideo.VideoId);
end;

procedure TFRMSGCTelegram.sgcTelegramNewChat(Sender: TObject;
  Chat: TsgcTelegramChat);
begin
  Chats.Add(Chat.Title + '=' + Chat.ChatId);
  listChats.AddItem(Chat.Title, nil);
end;

procedure TFRMSGCTelegram.Socks51Click(Sender: TObject);
begin
  sgcTelegram.AddProxySocks5(InputBox('Server', 'Set Server IP', ''),
    StrToInt(InputBox('Port', 'Set Server Port', '')),
    InputBox('Username', 'Set Username', ''),
    InputBox('Password', 'Set Password', ''));
end;

procedure TFRMSGCTelegram.SuperGroupDelete1Click(Sender: TObject);
begin
  sgcTelegram.DeleteSupergroup(StrToInt(InputBox('Delete Super Group',
    'Group Id', '0')));
end;

procedure TFRMSGCTelegram.SuperGroupsCreate1Click(Sender: TObject);
begin
  sgcTelegram.CreateNewSupergroupChat(InputBox('Create Super Group',
    'Title Group', 'Super Group Telegram'));
end;

procedure TFRMSGCTelegram.txtMessageKeyPress(Sender: TObject; var Key: Char);
begin
  if Key = Char(#$D) then
    btnSendMessage.Click();
end;

end.
```

