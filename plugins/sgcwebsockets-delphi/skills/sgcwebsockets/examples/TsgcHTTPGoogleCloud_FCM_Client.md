# TsgcHTTPGoogleCloud_FCM_Client - Example

Full source of `FGoogleFCM.pas` from the **20.HTTP_Protocol/03.Google/03.Google_FCM** demo, which uses `TsgcHTTPGoogleCloud_FCM_Client`.

API reference: [TsgcHTTPGoogleCloud_FCM_Client](../reference/api/TsgcHTTPGoogleCloud_FCM_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/03.Google_FCM` (file `FGoogleFCM.pas`)

```pascal
unit FGoogleFCM;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Vcl.StdCtrls, Vcl.ExtCtrls, sgcBase_Classes, sgcHTTP_Google_Cloud,
  sgcHTTP_Google_FCM, sgcHTTP, ComCtrls, sgcHTTP_Google_PubSub;

type
  TFRMGoogleFCM = class(TForm)
    memoLog: TMemo;
    pnlPublisher: TPanel;
    pnlTop: TPanel;
    GoogleFCM: TsgcHTTPGoogleCloud_FCM_Client;
    txtProject: TEdit;
    Label1: TLabel;
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
    memoPayload: TMemo;
    Label4: TLabel;
    btnSendMessage: TButton;
    procedure btnLoadJSONSettingsClick(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure FormCreate(Sender: TObject);
    procedure memoJWTPrivateKeyChange(Sender: TObject);
    procedure txtClientIdChange(Sender: TObject);
    procedure txtClientSecretChange(Sender: TObject);
    procedure txtJWTClientEmailChange(Sender: TObject);
    procedure txtJWTPrivateKeyIdChange(Sender: TObject);
  private
    FRefreshToken: Boolean;
    procedure DoLog(const aMethod, aText: string);
    procedure DoAuthenticate;
  end;

var
  FRMGoogleFCM: TFRMGoogleFCM;

implementation

uses
  INIFiles, sgcJSON;

{$R *.dfm}

procedure TFRMGoogleFCM.btnLoadJSONSettingsClick(Sender: TObject);
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    oDialog.Filter := 'JSON Files|*.json';
    if oDialog.Execute then
    begin
      GoogleFCM.LoadSettingsFromFile(oDialog.FileName);

      txtProject.Text := GoogleFCM.GoogleCloudOptions.JWT.ProjectId;
      txtJWTClientEmail.Text := GoogleFCM.GoogleCloudOptions.JWT.ClientEmail;
      txtJWTPrivateKeyId.Text := GoogleFCM.GoogleCloudOptions.JWT.PrivateKeyId;
      memoJWTPrivateKey.Lines.Text := GoogleFCM.GoogleCloudOptions.JWT.PrivateKey.Text;
    end;
  Finally
    oDialog.Free;
  End;
end;

procedure TFRMGoogleFCM.btnSendMessageClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLog('SendMessage', GoogleFCM.SendMessage(txtProject.text, memoPayload.lines.text));
end;

procedure TFRMGoogleFCM.FormCreate(Sender: TObject);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtClientId.Text := oINI.ReadString('OAUTH2', 'ClientId', '');
    txtClientSecret.Text := oINI.ReadString('OAUTH2', 'ClientSecret', '');
    txtProject.Text := oINI.ReadString('PROJECT', 'Project', '');
    txtJWTClientEmail.Text := oINI.ReadString('JWT', 'ClientEmail', '');
    txtJWTPrivateKeyId.Text := oINI.ReadString('JWT', 'PrivateKeyId', '');
  Finally
    oINI.Free;
  End;

  if FileExists('private_key.txt') then
    memoJWTPrivateKey.Lines.LoadFromFile('private_key.txt');
end;

procedure TFRMGoogleFCM.DoLog(const aMethod, aText: string);
begin
  memoLog.Lines.Add(aMethod + ': ' + aText);
end;

procedure TFRMGoogleFCM.DoAuthenticate;
var
  oINI: TINIFile;
  vToken: string;
begin
  if pageControl1.ActivePage = tabOAuth2 then
  begin
    GoogleFCM.GoogleCloudOptions.Authentication := gcaOAuth2;
    if not FRefreshToken then
    begin
      FRefreshToken := True;

      oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
      Try
        vToken := oINI.ReadString('OAUTH2', 'Token', '');
        if vToken <> '' then
          GoogleFCM.RefreshToken(vToken);
      Finally
        oINI.Free;
      End;
    end;
  end
  else if pageControl1.ActivePage = tabServiceAccount then
    GoogleFCM.GoogleCloudOptions.Authentication := gcaJWT;
end;

procedure TFRMGoogleFCM.FormClose(Sender: TObject; var Action: TCloseAction);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('OAUTH2', 'ClientId', txtClientId.Text);
    oINI.WriteString('OAUTH2', 'ClientSecret', txtClientSecret.Text);
    oINI.WriteString('PROJECT', 'Project', txtProject.Text);
    oINI.WriteString('JWT', 'ClientEmail', txtJWTClientEmail.Text);
    oINI.WriteString('JWT', 'PrivateKeyId', txtJWTPrivateKeyId.Text);

    memoJWTPrivateKey.Lines.SaveToFile('private_key.txt');
  Finally
    oINI.Free;
  End;
end;

procedure TFRMGoogleFCM.memoJWTPrivateKeyChange(Sender: TObject);
begin
  GoogleFCM.GoogleCloudOptions.JWT.PrivateKey.Text := memoJWTPrivateKey.Lines.Text;
end;

procedure TFRMGoogleFCM.txtClientIdChange(Sender: TObject);
begin
  GoogleFCM.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
end;

procedure TFRMGoogleFCM.txtClientSecretChange(Sender: TObject);
begin
  GoogleFCM.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;
end;

procedure TFRMGoogleFCM.txtJWTClientEmailChange(Sender: TObject);
begin
  GoogleFCM.GoogleCloudOptions.JWT.ClientEmail := txtJWTClientEmail.Text;
  GoogleFCM.GoogleCloudOptions.JWT.Subject := txtJWTClientEmail.Text;
end;

procedure TFRMGoogleFCM.txtJWTPrivateKeyIdChange(Sender: TObject);
begin
  GoogleFCM.GoogleCloudOptions.JWT.PrivateKeyId := txtJWTPrivateKeyId.Text;
end;

end.
```

