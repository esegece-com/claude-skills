# TsgcHTTPGoogleCloud_PubSub_Client - Example

Full source of `FGooglePubSub.pas` from the **20.HTTP_Protocol/03.Google/01.Google_PubSub** demo, which uses `TsgcHTTPGoogleCloud_PubSub_Client`.

API reference: [TsgcHTTPGoogleCloud_PubSub_Client](../reference/api/TsgcHTTPGoogleCloud_PubSub_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/01.Google_PubSub` (file `FGooglePubSub.pas`)

```pascal
unit FGooglePubSub;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Vcl.StdCtrls, Vcl.ExtCtrls, sgcBase_Classes, sgcHTTP_Google_Cloud,
  sgcHTTP_Google_PubSub, sgcHTTP, ComCtrls;

type
  TFRMGooglePubSub = class(TForm)
    memoLog: TMemo;
    pnlPublisher: TPanel;
    pnlTop: TPanel;
    GooglePubSub: TsgcHTTPGoogleCloud_PubSub_Client;
    pnlSubscriber: TPanel;
    btnCreateTopic: TButton;
    txtPublisherProject: TEdit;
    txtSubscriberProject: TEdit;
    Label1: TLabel;
    Label4: TLabel;
    txtPublisherTopic: TEdit;
    Label5: TLabel;
    btnDeleteTopic: TButton;
    btnListTopics: TButton;
    btnGetTopic: TButton;
    btnPublish: TButton;
    txtPublisherMessage: TEdit;
    RadioGroup1: TRadioGroup;
    Label6: TLabel;
    txtSubscriberSubscription: TEdit;
    btnCreateSubscription: TButton;
    btnDeleteSubscription: TButton;
    btnGetSubscription: TButton;
    btnListSubscriptions: TButton;
    txtSubscriberTopic: TEdit;
    Label7: TLabel;
    txtPull: TButton;
    btnAcknowledge: TButton;
    txtAckId: TEdit;
    GroupBox1: TGroupBox;
    PageControl1: TPageControl;
    tabOAuth2: TTabSheet;
    Label2: TLabel;
    Label3: TLabel;
    RadioGroup2: TRadioGroup;
    txtClientId: TEdit;
    txtClientSecret: TEdit;
    tabServiceAccount: TTabSheet;
    txtJWTClientEmail: TEdit;
    txtJWTPrivateKeyId: TEdit;
    memoJWTPrivateKey: TMemo;
    Label8: TLabel;
    Label9: TLabel;
    Label10: TLabel;
    btnLoadJSONSettings: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnAcknowledgeClick(Sender: TObject);
    procedure btnCreateSubscriptionClick(Sender: TObject);
    procedure btnCreateTopicClick(Sender: TObject);
    procedure btnDeleteSubscriptionClick(Sender: TObject);
    procedure btnDeleteTopicClick(Sender: TObject);
    procedure btnGetSubscriptionClick(Sender: TObject);
    procedure btnGetTopicClick(Sender: TObject);
    procedure btnListSubscriptionsClick(Sender: TObject);
    procedure btnListTopicsClick(Sender: TObject);
    procedure btnLoadJSONSettingsClick(Sender: TObject);
    procedure btnPublishClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure GooglePubSubAuthToken(Sender: TObject; const TokenType, Token, Data:
        string);
    procedure memoJWTPrivateKeyChange(Sender: TObject);
    procedure txtClientIdChange(Sender: TObject);
    procedure txtClientSecretChange(Sender: TObject);
    procedure txtJWTClientEmailChange(Sender: TObject);
    procedure txtJWTPrivateKeyIdChange(Sender: TObject);
    procedure txtPullClick(Sender: TObject);
  private
    FRefreshToken: Boolean;
    procedure DoLog(const aMethod, aText: string);
    procedure DoAuthenticate;
  end;

var
  FRMGooglePubSub: TFRMGooglePubSub;

implementation

uses
  INIFiles, sgcJSON;

{$R *.dfm}

procedure TFRMGooglePubSub.FormCreate(Sender: TObject);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtClientId.Text := oINI.ReadString('OAUTH2', 'ClientId', '');
    txtClientSecret.Text := oINI.ReadString('OAUTH2', 'ClientSecret', '');
    txtPublisherProject.Text := oINI.ReadString('PROJECT', 'PublisherProject', '');
    txtSubscriberProject.Text := oINI.ReadString('PROJECT', 'SubscriberProject', '');
    txtJWTClientEmail.Text := oINI.ReadString('JWT', 'ClientEmail', '');
    txtJWTPrivateKeyId.Text := oINI.ReadString('JWT', 'PrivateKeyId', '');
  Finally
    oINI.Free;
  End;

  if FileExists('private_key.txt') then
    memoJWTPrivateKey.Lines.LoadFromFile('private_key.txt');
end;

procedure TFRMGooglePubSub.btnAcknowledgeClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#Acknowledge', GooglePubSub.Acknowledge
    (txtSubscriberProject.Text, txtSubscriberSubscription.Text,
    txtAckId.Text));
end;

procedure TFRMGooglePubSub.btnCreateSubscriptionClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#CreateSubscription', GooglePubSub.CreateSubscription
    (txtSubscriberProject.Text, txtSubscriberSubscription.Text,
    txtSubscriberTopic.Text));
end;

procedure TFRMGooglePubSub.btnCreateTopicClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#CreateTopic', GooglePubSub.CreateTopic(txtPublisherProject.Text,
    txtPublisherTopic.Text));
end;

procedure TFRMGooglePubSub.btnDeleteSubscriptionClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#DeleteSubscription', GooglePubSub.DeleteSubscripton
    (txtSubscriberProject.Text, txtSubscriberSubscription.Text));
end;

procedure TFRMGooglePubSub.btnDeleteTopicClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#DeleteTopic', GooglePubSub.DeleteTopic(txtPublisherProject.Text,
    txtPublisherTopic.Text));
end;

procedure TFRMGooglePubSub.btnGetSubscriptionClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#GetSubscription',
    GooglePubSub.GetSubscription(txtSubscriberProject.Text,
    txtSubscriberSubscription.Text));
end;

procedure TFRMGooglePubSub.btnGetTopicClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#GetTopic', GooglePubSub.GetTopic(txtPublisherProject.Text,
    txtPublisherTopic.Text));
end;

procedure TFRMGooglePubSub.btnListSubscriptionsClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#ListSubscriptions', GooglePubSub.ListSubscriptions
    (txtSubscriberProject.Text));
end;

procedure TFRMGooglePubSub.btnListTopicsClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#ListTopics', GooglePubSub.ListTopics(txtPublisherProject.Text));
end;

procedure TFRMGooglePubSub.btnLoadJSONSettingsClick(Sender: TObject);
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    oDialog.Filter := 'JSON Files|*.json';
    if oDialog.Execute then
    begin
      GooglePubSub.LoadSettingsFromFile(oDialog.FileName);

      txtPublisherProject.Text := GooglePubSub.GoogleCloudOptions.JWT.ProjectId;
      txtSubscriberProject.Text := GooglePubSub.GoogleCloudOptions.JWT.ProjectId;
      txtJWTClientEmail.Text := GooglePubSub.GoogleCloudOptions.JWT.ClientEmail;
      txtJWTPrivateKeyId.Text := GooglePubSub.GoogleCloudOptions.JWT.PrivateKeyId;
      memoJWTPrivateKey.Lines.Text := GooglePubSub.GoogleCloudOptions.JWT.PrivateKey.Text;
    end;
  Finally
    oDialog.Free;
  End;
end;

procedure TFRMGooglePubSub.btnPublishClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#Publish', GooglePubSub.Publish(txtPublisherProject.Text,
    txtPublisherTopic.Text, txtPublisherMessage.Text));
end;

procedure TFRMGooglePubSub.DoLog(const aMethod, aText: string);
begin
  memoLog.Lines.Add(aMethod + ': ' + aText);
end;

procedure TFRMGooglePubSub.DoAuthenticate;
var
  oINI: TINIFile;
  vToken: string;
begin
  if pageControl1.ActivePage = tabOAuth2 then
  begin
    GooglePubSub.GoogleCloudOptions.Authentication := gcaOAuth2;
    if not FRefreshToken then
    begin
      FRefreshToken := True;

      oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
      Try
        vToken := oINI.ReadString('OAUTH2', 'Token', '');
        if vToken <> '' then
          GooglePubSub.RefreshToken(vToken);
      Finally
        oINI.Free;
      End;
    end;
  end
  else if pageControl1.ActivePage = tabServiceAccount then
    GooglePubSub.GoogleCloudOptions.Authentication := gcaJWT;
end;

procedure TFRMGooglePubSub.FormClose(Sender: TObject; var Action: TCloseAction);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('OAUTH2', 'ClientId', txtClientId.Text);
    oINI.WriteString('OAUTH2', 'ClientSecret', txtClientSecret.Text);
    oINI.WriteString('PROJECT', 'PublisherProject', txtPublisherProject.Text);
    oINI.WriteString('PROJECT', 'SubscriberProject', txtSubscriberProject.Text);
    oINI.WriteString('JWT', 'ClientEmail', txtJWTClientEmail.Text);
    oINI.WriteString('JWT', 'PrivateKeyId', txtJWTPrivateKeyId.Text);

    memoJWTPrivateKey.Lines.SaveToFile('private_key.txt');
  Finally
    oINI.Free;
  End;
end;

procedure TFRMGooglePubSub.GooglePubSubAuthToken(Sender: TObject; const
    TokenType, Token, Data: string);
var
  oINI: TINIFile;
  oJSON: TsgcJSON;
begin
  oJSON := TsgcJSON.Create(nil);
  Try
    oJSON.Read(Data);
    if oJSON.Node['refresh_token'] <> nil then
    begin
      oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
      Try
        oINI.WriteString('OAUTH2', 'Token', oJSON.Node['refresh_token'].Value);
      Finally
        oINI.Free;
      End;
    end;
  Finally
    oJSON.Free;
  End;
end;

procedure TFRMGooglePubSub.memoJWTPrivateKeyChange(Sender: TObject);
begin
  GooglePubSub.GoogleCloudOptions.JWT.PrivateKey.Text := memoJWTPrivateKey.Lines.Text;
end;

procedure TFRMGooglePubSub.txtClientIdChange(Sender: TObject);
begin
  GooglePubSub.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
end;

procedure TFRMGooglePubSub.txtClientSecretChange(Sender: TObject);
begin
  GooglePubSub.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;
end;

procedure TFRMGooglePubSub.txtJWTClientEmailChange(Sender: TObject);
begin
  GooglePubSub.GoogleCloudOptions.JWT.ClientEmail := txtJWTClientEmail.Text;
end;

procedure TFRMGooglePubSub.txtJWTPrivateKeyIdChange(Sender: TObject);
begin
  GooglePubSub.GoogleCloudOptions.JWT.PrivateKeyId := txtJWTPrivateKeyId.Text;
end;

procedure TFRMGooglePubSub.txtPullClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('#Pull', GooglePubSub.Pull(txtSubscriberProject.Text,
    txtSubscriberSubscription.Text));
end;

end.
```

