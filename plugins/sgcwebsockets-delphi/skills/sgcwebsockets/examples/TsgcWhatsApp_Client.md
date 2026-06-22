# TsgcWhatsApp_Client - Example

Full source of `FWhatsApp.pas` from the **50.Other/05.WhatsApp** demo, which uses `TsgcWhatsApp_Client`.

API reference: [TsgcWhatsApp_Client](../reference/api/TsgcWhatsApp_Client.md)
Source demo: `50.Other/05.WhatsApp` (file `FWhatsApp.pas`)

```pascal
unit FWhatsApp;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Vcl.StdCtrls, sgcBase_Classes, sgcLib_WhatsApp_Client, sgcLibs,
  Vcl.ExtCtrls, sgcLib_Whatsapp;

type
  TsgcWhatsAppNumbers = class(TsgcThreadSafeBase)
  private
    FList: TStringList;
    function GetList: TStringList;
  protected
    property List: TStringList read GetList write FList;
  public
    constructor Create; override;
    destructor Destroy; override;
    function AddNumber(aValue: string): Boolean;
  private
    function GetFileName: string;
  public
    property FileName: string read GetFileName;
  end;

  TFRMWhatsApp = class(TForm)
    pnlTop: TPanel;
    pnlBody: TPanel;
    txtPhoneNumberId: TEdit;
    whatsapp: TsgcWhatsApp_Client;
    Label1: TLabel;
    Label2: TLabel;
    txtToken: TEdit;
    pnlBottom: TPanel;
    memoLog: TMemo;
    btnSendMessage: TButton;
    txtMessageText: TEdit;
    txtMessagePhone: TEdit;
    Label3: TLabel;
    Label4: TLabel;
    GroupBox1: TGroupBox;
    GroupBox2: TGroupBox;
    Label5: TLabel;
    Label6: TLabel;
    txtServerIP: TEdit;
    txtServerPort: TEdit;
    chkServerSSL: TCheckBox;
    Label7: TLabel;
    txtServerCertificate: TEdit;
    Label8: TLabel;
    txtServerKeyFile: TEdit;
    Label9: TLabel;
    txtServerWebhookEndpoint: TEdit;
    Label10: TLabel;
    txtServerWebhookToken: TEdit;
    btnStartServer: TButton;
    btnStopServer: TButton;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure btnStartServerClick(Sender: TObject);
    procedure btnStopServerClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure whatsappMessageReceived(Sender: TObject;
      const aMessage: TsgcWhatsApp_Receive_Message; var aMarkAsRead: Boolean);
    procedure whatsappMessageSent(Sender: TObject;
      const aMessage: TsgcWhatsApp_Receive_Message;
      aStatus: TsgcWhatsAppSendMessageStatusType);
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  private
    FWhatsAppNumbers: TsgcWhatsAppNumbers;
    function GetWhatsAppNumbers: TsgcWhatsAppNumbers;
  protected
    property WhatsAppNumbers: TsgcWhatsAppNumbers read GetWhatsAppNumbers
      write FWhatsAppNumbers;
  protected
    procedure DoLog(const aText: string);
  protected
    procedure DoWhatsApp_ButtonReply(const aTo: string;
      const aButtonReply
      : TsgcWhatsApp_Receive_Message_Message_Interactive_ButtonReply);
    procedure DoWhatsApp_Echo(const aTo, aText: string);
    procedure DoWhatsApp_Message(const aTo, aText: string);
    procedure DoWhatsApp_ListReply(const aTo: string;
      const aListReply
      : TsgcWhatsApp_Receive_Message_Message_Interactive_ListReply);
    procedure DoWhatsApp_Welcome(const aTo: string);
  public
    { Public declarations }
  end;

var
  FRMWhatsApp: TFRMWhatsApp;

implementation

uses
  INIFiles,
  sgcBase_Helpers, sgcWebSocket_Types;

{$R *.dfm}

procedure TFRMWhatsApp.FormCreate(Sender: TObject);
begin
  DoLoadSettings;

  // ... using neAsynchronous to update the memo control
  // ... in production set the value neNoSync
  whatsapp.NotifyEvents := neAsynchronous;
end;

procedure TFRMWhatsApp.FormDestroy(Sender: TObject);
begin
  sgcFree(FWhatsAppNumbers);
end;

procedure TFRMWhatsApp.btnSendMessageClick(Sender: TObject);
begin
  whatsapp.WhatsappOptions.PhoneNumberId := txtPhoneNumberId.Text;
  whatsapp.WhatsappOptions.Token := txtToken.Text;

  DoLog('Message Sent: ' + whatsapp.SendMessageLocation(txtMessagePhone.Text,
    '10', '2', 'My Address', 'C/ La Pau 79 Manresa'));

  txtMessageText.Text := '';
end;

procedure TFRMWhatsApp.btnStartServerClick(Sender: TObject);
begin
  whatsapp.ServerOptions.IP := txtServerIP.Text;
  whatsapp.ServerOptions.Port := StrToInt(txtServerPort.Text);
  whatsapp.ServerOptions.SSL := chkServerSSL.Checked;
  if whatsapp.ServerOptions.SSL then
  begin
    whatsapp.ServerOptions.SSLOptions.CertFile := txtServerCertificate.Text;
    whatsapp.ServerOptions.SSLOptions.KeyFile := txtServerKeyFile.Text;
    whatsapp.ServerOptions.SSLOptions.Port := StrToInt(txtServerPort.Text);
  end;
  whatsapp.ServerOptions.WebhookOptions.Endpoint :=
    txtServerWebhookEndpoint.Text;
  whatsapp.ServerOptions.WebhookOptions.Token := txtServerWebhookToken.Text;

  whatsapp.WhatsappOptions.PhoneNumberId := txtPhoneNumberId.Text;
  whatsapp.WhatsappOptions.Token := txtToken.Text;

  whatsapp.StartServer;
end;

procedure TFRMWhatsApp.btnStopServerClick(Sender: TObject);
begin
  whatsapp.StopServer;
end;

procedure TFRMWhatsApp.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtPhoneNumberId.Text := oINI.ReadString('WhatsAppOptions',
      'PhoneNumberId', '');
    txtToken.Text := oINI.ReadString('WhatsAppOptions', 'Token', '');

    txtServerIP.Text := oINI.ReadString('ServerOptions', 'IP', '');
    txtServerPort.Text := IntToStr(oINI.ReadInteger('ServerOptions',
      'Port', 1337));
    chkServerSSL.Checked := oINI.ReadBool('ServerOptions', 'SSL', True);
    txtServerCertificate.Text := oINI.ReadString('ServerOptions',
      'Certificate', '');
    txtServerKeyFile.Text := oINI.ReadString('ServerOptions', 'KeyFile', '');

    txtServerWebhookEndpoint.Text := oINI.ReadString('ServerOptions.WebHook',
      'Endpoint', '');
    txtServerWebhookToken.Text := oINI.ReadString('ServerOptions.WebHook',
      'Token', '');

    txtMessagePhone.Text := oINI.ReadString('Messages', 'Phone', '');
  Finally
    FreeAndNil(oINI);
  End;
end;

procedure TFRMWhatsApp.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText)
end;

procedure TFRMWhatsApp.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('WhatsAppOptions', 'PhoneNumberId', txtPhoneNumberId.Text);
    oINI.WriteString('WhatsAppOptions', 'Token', txtToken.Text);

    oINI.WriteString('ServerOptions', 'IP', txtServerIP.Text);
    oINI.WriteInteger('ServerOptions', 'Port', StrToInt(txtServerPort.Text));
    oINI.WriteBool('ServerOptions', 'SSL', chkServerSSL.Checked);
    oINI.WriteString('ServerOptions', 'Certificate', txtServerCertificate.Text);
    oINI.WriteString('ServerOptions', 'KeyFile', txtServerKeyFile.Text);

    oINI.WriteString('ServerOptions.WebHook', 'Endpoint',
      txtServerWebhookEndpoint.Text);
    oINI.WriteString('ServerOptions.WebHook', 'Token',
      txtServerWebhookToken.Text);

    oINI.WriteString('Messages', 'Phone', txtMessagePhone.Text);
  Finally
    FreeAndNil(oINI);
  End;
end;

procedure TFRMWhatsApp.DoWhatsApp_ButtonReply(const aTo: string;
  const aButtonReply
  : TsgcWhatsApp_Receive_Message_Message_Interactive_ButtonReply);
begin
  if aButtonReply.Id = 'Delphi' then
    whatsapp.SendMessageText(aTo,
      sgcDecodeJSON('\ud83d\udc4d\ud83d\udc4d\ud83d\udc4d'))
  else if aButtonReply.Id = 'C++' then
    whatsapp.SendMessageText(aTo,
      sgcDecodeJSON('\ud83d\udc4f\ud83d\udc4f\ud83d\udc4f'))
  else
    whatsapp.SendMessageText(aTo,
      sgcDecodeJSON('\ud83d\ude31\ud83d\ude31\ud83d\ude31'));
end;

procedure TFRMWhatsApp.DoWhatsApp_Echo(const aTo, aText: string);
begin
  whatsapp.SendMessageText(aTo, 'ECHO ==> ' + aText);
end;

procedure TFRMWhatsApp.DoWhatsApp_ListReply(const aTo: string;
  const aListReply: TsgcWhatsApp_Receive_Message_Message_Interactive_ListReply);
begin
  if aListReply.Id = 'receive_message_text' then
    whatsapp.SendMessageText(aTo, 'Sample Message Sent by eSeGeCe Bot')
  else if aListReply.Id = 'receive_message_image' then
    whatsapp.SendMessageImage(aTo,
      'https://www.esegece.com/images/esegece.png', 'Logo')
  else if aListReply.Id = 'receive_message_document' then
    whatsapp.SendMessageDocument(aTo,
      'https://www.esegece.com/manual/sgcWebSockets/delphi', 'Document',
      'sgcWebSockets.pdf')
  else if aListReply.Id = 'receive_message_contact' then
    whatsapp.SendMessageContact(aTo, 'eSeGeCe', '34613057691',
      'info@esegece.com')
  else if aListReply.Id = 'receive_message_button' then
    whatsapp.SendMessageInteractiveButtons(aTo, 'eSeGeCe',
      'Which is your favourite programming language?',
      'Powered by sgcWebSockets', 'Options', ['Delphi', 'C++', 'Other']);
end;

procedure TFRMWhatsApp.DoWhatsApp_Message(const aTo, aText: string);
begin
  whatsapp.SendMessageText(aTo, aText);
end;

procedure TFRMWhatsApp.DoWhatsApp_Welcome(const aTo: string);
var
  oMessage: TsgcWhatsapp_Send_Message_Interactive;
begin
  oMessage := TsgcWhatsapp_Send_Message_Interactive.Create;
  Try

    oMessage.InteractiveType := wapitList;
    oMessage.Header._Type := waphtText;
    oMessage.Header.Text := 'eSeGeCe';
    oMessage.Body.Text :=
      'Welcome to eSeGeCe!!! This message demonstrates your ability to send a message notification from WhatsApp Business Platform''s Cloud API using sgcWebSockets Component. '
      + 'Next Text Messages will be echoed to you. Find below a list of options to test the eSeGeCe Bot.';
    oMessage.Footer.Text := 'Powered by sgcWebSockets';
    oMessage.Action.Button := 'Options';
    oMessage.Action.Sections.Section1.Title := 'Receive Messages';
    oMessage.Action.Sections.Section1.Rows.Row1.Id := 'receive_message_text';
    oMessage.Action.Sections.Section1.Rows.Row1.Title := 'Text';
    oMessage.Action.Sections.Section1.Rows.Row1.Description :=
      'Receive a sample text message.';
    oMessage.Action.Sections.Section1.Rows.Row2.Id := 'receive_message_image';
    oMessage.Action.Sections.Section1.Rows.Row2.Title := 'Image';
    oMessage.Action.Sections.Section1.Rows.Row2.Description :=
      'Receive a sample Image message.';
    oMessage.Action.Sections.Section1.Rows.Row3.Id :=
      'receive_message_document';
    oMessage.Action.Sections.Section1.Rows.Row3.Title := 'Document';
    oMessage.Action.Sections.Section1.Rows.Row3.Description :=
      'Receive a sample Document message.';
    oMessage.Action.Sections.Section1.Rows.Row4.Id := 'receive_message_contact';
    oMessage.Action.Sections.Section1.Rows.Row4.Title := 'Contact';
    oMessage.Action.Sections.Section1.Rows.Row4.Description :=
      'Receive a sample Contact message.';
    oMessage.Action.Sections.Section1.Rows.Row5.Id := 'receive_message_button';
    oMessage.Action.Sections.Section1.Rows.Row5.Title := 'Buttons';
    oMessage.Action.Sections.Section1.Rows.Row5.Description :=
      'Receive a sample Interactive Buttons message.';

    whatsapp.SendMessage(aTo, oMessage);
  Finally
    sgcFree(oMessage);
  End;
end;

procedure TFRMWhatsApp.FormClose(Sender: TObject; var Action: TCloseAction);
begin
  DoSaveSettings;
end;

function TFRMWhatsApp.GetWhatsAppNumbers: TsgcWhatsAppNumbers;
begin
  if not Assigned(FWhatsAppNumbers) then
    FWhatsAppNumbers := TsgcWhatsAppNumbers.Create;
  Result := FWhatsAppNumbers;
end;

procedure TFRMWhatsApp.whatsappMessageReceived(Sender: TObject;
  const aMessage: TsgcWhatsApp_Receive_Message; var aMarkAsRead: Boolean);
var
  vTo: string;
begin
  if aMessage.Contacts.Count > 0 then
  begin
    vTo := aMessage.Contacts.Contact[0].WaID;

    DoLog('Message Received: ' + aMessage.Messages._Message[0].Id);

    if WhatsAppNumbers.AddNumber(vTo) then
      DoWhatsApp_Welcome(vTo)
    else if aMessage.Messages.Count > 0 then
    begin
      case aMessage.Messages._Message[0]._Type of
        wapmrtText:
          begin
            DoWhatsApp_Echo(vTo, aMessage.Messages._Message[0].Text.Body);
            DoLog(aMessage.Messages._Message[0].Text.Body);

            aMarkAsRead := True;
          end;
        wapmrtAudio:
          begin
            DoWhatsApp_Message(vTo, 'Thanks for the audio!!!');
            aMarkAsRead := True;
          end;
        wapmrtDocument:
          begin
            DoWhatsApp_Message(vTo, 'Thanks for the document!!!');
            aMarkAsRead := True;
          end;
        wapmrtImage:
          begin
            DoWhatsApp_Message(vTo, 'Thanks for the image!!!');
            aMarkAsRead := True;
          end;
        wapmrtSticker:
          begin
            DoWhatsApp_Message(vTo, 'Thanks for the sticker!!!');
            aMarkAsRead := True;
          end;
        wapmrtVideo:
          begin
            DoWhatsApp_Message(vTo, 'Thanks for the video!!!');
            aMarkAsRead := True;
          end;
        wapmrtInteractive:
          begin
            if aMessage.Messages._Message[0].Interactive._Type = wapmirListReply
            then
            begin
              DoWhatsApp_ListReply(vTo, aMessage.Messages._Message[0]
                .Interactive.ListReply);
            end
            else if aMessage.Messages._Message[0].Interactive._Type = wapmirButtonReply
            then
            begin
              DoWhatsApp_ButtonReply(vTo, aMessage.Messages._Message[0]
                .Interactive.ButtonReply);
            end;
            aMarkAsRead := True;
          end;
        wapmrtLocation:
          begin
            DoWhatsApp_Message(vTo,
              Format('Thanks for sending your location!!! Latitude: [%s] Longitude: [%s]',
              [aMessage.Messages._Message[0].Location.Latitude,
              aMessage.Messages._Message[0].Location.Longitude]));
            aMarkAsRead := True;
          end;
      end;
    end;
  end;
end;

procedure TFRMWhatsApp.whatsappMessageSent(Sender: TObject;
  const aMessage: TsgcWhatsApp_Receive_Message;
  aStatus: TsgcWhatsAppSendMessageStatusType);
var
  vStatus: string;
begin
  case aStatus of
    wapsmstUnknown:
      vStatus := 'unknown';
    wapsmstSent:
      vStatus := 'sent';
    wapsmstDelivered:
      vStatus := 'delivered';
    wapsmstRead:
      vStatus := 'read';
  end;
  DoLog('Message Sent: ' + aMessage.Statuses.Status[0].Id + ' ' + vStatus);
end;

constructor TsgcWhatsAppNumbers.Create;
begin
  inherited;
  if FileExists(FileName) then
    List.LoadFromFile(FileName);
end;

destructor TsgcWhatsAppNumbers.Destroy;
begin
  if Assigned(FList) then
  begin
    FList.SaveToFile(FileName);
    sgcFree(FList);
  end;
  inherited;
end;

function TsgcWhatsAppNumbers.AddNumber(aValue: string): Boolean;
begin
  DoEnterCS;
  Try
    Result := List.IndexOf(aValue) < 0;
    if Result then
      List.Add(aValue);
  Finally
    DoLeaveCS;
  End;
end;

function TsgcWhatsAppNumbers.GetFileName: string;
begin
  Result := ExtractFilePath(Application.ExeName) + 'whatsapp_numbers.txt';
end;

function TsgcWhatsAppNumbers.GetList: TStringList;
begin
  if not Assigned(FList) then
  begin
    FList := TStringList.Create;
    FList.Sorted := True;
    FList.Duplicates := dupIgnore;
  end;
  Result := FList;
end;

end.
```

