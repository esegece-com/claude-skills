# TsgcIoTAmazon_MQTT_Client - Example

Full source of `FsgcClientIoT.pas` from the **10.IoT_Clients** demo, which uses `TsgcIoTAmazon_MQTT_Client`.

API reference: [TsgcIoTAmazon_MQTT_Client](../reference/api/TsgcIoTAmazon_MQTT_Client.md)
Source demo: `10.IoT_Clients` (file `FsgcClientIoT.pas`)

```pascal
unit FsgcClientIoT;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ComCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcIoT_Classes,
  sgcIoT_Client, sgcIoT_MQTT_Client, sgcIoT_Amazon_MQTT_Client, sgcIoT,
  sgcWebSocket_Classes, sgcWebSocket_Types, sgcWebSocket_Protocol_MQTT_Message,
  sgcIoT_Azure_MQTT_Client, sgcTCP_Classes, sgcSocket_Classes,
  sgcIoT_Azure_HTTP_Client;

type
  TFRMSGCClientIoT = class(TForm)
    pnlClient: TPanel;
    pnlMemo: TPanel;
    memoLog: TMemo;
    PageControl1: TPageControl;
    tabAMAZON: TTabSheet;
    Label1: TLabel;
    Label12: TLabel;
    btnSubscribeAmazon: TButton;
    btnUnsubscribeAmazon: TButton;
    txtChannelAmazon: TEdit;
    btnPublishAmazon: TButton;
    txtPublishChannelAmazon: TEdit;
    txtPublishMessageAmazon: TEdit;
    cboQoSAmazon: TComboBox;
    AmazonIoT: TsgcIoTAmazon_MQTT_Client;
    btnAmazonConnect: TButton;
    btnAmazonDisconnect: TButton;
    txtAmazonEndpoint: TEdit;
    Label3: TLabel;
    Label4: TLabel;
    txtAmazonClientId: TEdit;
    Label5: TLabel;
    txtAmazonCertfile: TEdit;
    txtAmazonKeyFile: TEdit;
    Label6: TLabel;
    btnSubscribeAmazonClientConnected: TButton;
    btnSubscribeAmazonClientDisconnected: TButton;
    btnSubscribeAmazonClientSubscribed: TButton;
    btnSubscribeAmazonClientUnSubscribed: TButton;
    txtAmazonClientIdEvents: TEdit;
    Label2: TLabel;
    Label7: TLabel;
    Label8: TLabel;
    Label9: TLabel;
    tabAzure: TTabSheet;
    Label10: TLabel;
    btnAzureConnect: TButton;
    btnAzureDisconnect: TButton;
    txtAzureIoTHub: TEdit;
    Label11: TLabel;
    Label13: TLabel;
    txtAzureCertfile: TEdit;
    txtAzureKeyFile: TEdit;
    Label14: TLabel;
    txtAzureDeviceId: TEdit;
    Label15: TLabel;
    AzureIoT: TsgcIoTAzure_MQTT_Client;
    txtAzureSecretKey: TEdit;
    Label16: TLabel;
    Label17: TLabel;
    btnAzureSubscribeCloudToDevice: TButton;
    btnAzureUnsubscribeCloudToDevice: TButton;
    Label18: TLabel;
    txtPublishMessageAzure: TEdit;
    btnAzureSendDeviceToCloud: TButton;
    cboQoSAzure: TComboBox;
    Label19: TLabel;
    Label20: TLabel;
    btnAzureSubscribeDeviceTwins: TButton;
    btnAzureGetDeviceTwinsProperties: TButton;
    btnAzureUnSubscribeDeviceTwins: TButton;
    btnAzureSetDeviceTwinsProperties: TButton;
    txtAzureSetDeviceTwinsProperties: TEdit;
    btnAzureSubscribeDirectMethod: TButton;
    btnAzureUnSubscribeDirectMethod: TButton;
    btnAzureRespondPublicMethod: TButton;
    txtAzureRespondPublicMethodStatus: TEdit;
    Label22: TLabel;
    txtAzureRespondPublicMethodText: TEdit;
    txtAzureRespondPublicMethodRequestId: TEdit;
    Label23: TLabel;
    cboAmazonAuthentication: TComboBox;
    Label21: TLabel;
    txtAmazonRegion: TEdit;
    txtAmazonAccessKey: TEdit;
    txtAmazonSecretKey: TEdit;
    Label24: TLabel;
    Label25: TLabel;
    Label26: TLabel;
    txtAmazonParameters: TEdit;
    txtAmazonHeaders: TEdit;
    chkAmazonWebSockets: TCheckBox;
    Label27: TLabel;
    Label28: TLabel;
    Label29: TLabel;
    Label30: TLabel;
    txtAmazonSessionToken: TEdit;
    Label31: TLabel;
    cboAzureAuthentication: TComboBox;
    Label32: TLabel;
    btnAzureFileUpload: TButton;
    Label33: TLabel;
    txtAzureKeyName: TEdit;
    btnAzureProvisioningDeviceClientRegister: TButton;
    Label34: TLabel;
    Label35: TLabel;
    txtAzureProvisioningScopeId: TEdit;
    txtAzureProvisioningRegistrationId: TEdit;
    Label36: TLabel;
    Label37: TLabel;
    btnRegisterThingAmazon: TButton;
    txtRegisterThingTemplateAmazon: TEdit;
    Label38: TLabel;
    Label39: TLabel;
    btnCreateCertificateFromCsrAmazon: TButton;
    btnSubscribeCreateCertificateFromCsr: TButton;
    txtCertificateSigningRequestAmazon: TEdit;
    Label40: TLabel;
    btnCreateKeysAndCertificateAmazon: TButton;
    btnSubscribeCreateKeysAndCertificateAmazon: TButton;
    btnSubscribeRegisterThingAmazon: TButton;
    memoRegisterThingPayloadAmazon: TMemo;
    procedure AmazonIoTConnect(Connection: TsgcWSConnection);
    procedure AmazonIoTDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure AmazonIoTMQTTConnect(Connection: TsgcWSConnection;
      const Session: Boolean; const ReasonCode: Integer;
      const ReasonName: string;
      const ConnectProperties: TsgcWSMQTTCONNACKProperties);
    procedure AmazonIoTMQTTDisconnect(Connection: TsgcWSConnection;
      ReasonCode: Integer; const ReasonName: string;
      DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
    procedure AmazonIoTMQTTPublish(Connection: TsgcWSConnection;
      aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
    procedure AmazonIoTMQTTSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
      SubscribeProperties: TsgcWSMQTTSUBACKProperties);
    procedure AmazonIoTMQTTUnSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS;
      UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
    procedure AzureIoTConnect(Connection: TsgcWSConnection);
    procedure AzureIoTDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure AzureIoTMQTTConnect(Connection: TsgcWSConnection;
      const Session: Boolean; const ReasonCode: Integer;
      const ReasonName: string;
      const ConnectProperties: TsgcWSMQTTCONNACKProperties);
    procedure AzureIoTMQTTDisconnect(Connection: TsgcWSConnection;
      ReasonCode: Integer; const ReasonName: string;
      DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
    procedure AzureIoTMQTTPublish(Connection: TsgcWSConnection;
      aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
    procedure AzureIoTMQTTSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
      SubscribeProperties: TsgcWSMQTTSUBACKProperties);
    procedure AzureIoTMQTTUnSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS;
      UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
    procedure btnAmazonConnectClick(Sender: TObject);
    procedure btnAmazonDisconnectClick(Sender: TObject);
    procedure btnAzureConnectClick(Sender: TObject);
    procedure btnAzureDisconnectClick(Sender: TObject);
    procedure btnAzureFileUploadClick(Sender: TObject);
    procedure btnAzureSendDeviceToCloudClick(Sender: TObject);
    procedure btnAzureSubscribeCloudToDeviceClick(Sender: TObject);
    procedure btnAzureSubscribeDeviceTwinsClick(Sender: TObject);
    procedure btnAzureUnsubscribeCloudToDeviceClick(Sender: TObject);
    procedure btnAzureUnSubscribeDeviceTwinsClick(Sender: TObject);
    procedure btnPublishAmazonClick(Sender: TObject);
    procedure btnSubscribeAmazonClick(Sender: TObject);
    procedure btnSubscribeAmazonClientConnectedClick(Sender: TObject);
    procedure btnSubscribeAmazonClientDisconnectedClick(Sender: TObject);
    procedure btnSubscribeAmazonClientSubscribedClick(Sender: TObject);
    procedure btnSubscribeAmazonClientUnSubscribedClick(Sender: TObject);
    procedure btnUnsubscribeAmazonClick(Sender: TObject);
    procedure btnAzureGetDeviceTwinsPropertiesClick(Sender: TObject);
    procedure btnAzureRespondPublicMethodClick(Sender: TObject);
    procedure btnAzureSetDeviceTwinsPropertiesClick(Sender: TObject);
    procedure btnAzureSubscribeDirectMethodClick(Sender: TObject);
    procedure btnAzureUnSubscribeDirectMethodClick(Sender: TObject);
    procedure btnAzureProvisioningDeviceClientRegisterClick(Sender: TObject);
    procedure btnCreateCertificateFromCsrAmazonClick(Sender: TObject);
    procedure btnCreateKeysAndCertificateAmazonClick(Sender: TObject);
    procedure btnRegisterThingAmazonClick(Sender: TObject);
    procedure btnSubscribeCreateCertificateFromCsrClick(Sender: TObject);
    procedure btnSubscribeCreateKeysAndCertificateAmazonClick(Sender: TObject);
    procedure btnSubscribeRegisterThingAmazonClick(Sender: TObject);
    procedure cboAmazonAuthenticationChange(Sender: TObject);
    procedure cboAzureAuthenticationChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoInitialize;
  public
    { Public declarations }
  end;

var
  FRMSGCClientIoT: TFRMSGCClientIoT;

implementation

{$R *.dfm}

procedure TFRMSGCClientIoT.AmazonIoTConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected Socket');
end;

procedure TFRMSGCClientIoT.AmazonIoTDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected Socket');
end;

procedure TFRMSGCClientIoT.AmazonIoTMQTTConnect(Connection: TsgcWSConnection;
  const Session: Boolean; const ReasonCode: Integer; const ReasonName: string;
  const ConnectProperties: TsgcWSMQTTCONNACKProperties);
begin
  DoLog('#connected AWS IoT Broker');
end;

procedure TFRMSGCClientIoT.AmazonIoTMQTTDisconnect(Connection: TsgcWSConnection;
  ReasonCode: Integer; const ReasonName: string;
  DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
begin
  DoLog('#disconnected AWS IoT Broker');
end;

procedure TFRMSGCClientIoT.AmazonIoTMQTTPublish(Connection: TsgcWSConnection;
  aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
begin
  DoLog('Received Message: ' + aTopic + ' ' + aText);
end;

procedure TFRMSGCClientIoT.AmazonIoTMQTTSubscribe(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
  SubscribeProperties: TsgcWSMQTTSUBACKProperties);
begin
  DoLog('#subscribed');
end;

procedure TFRMSGCClientIoT.AmazonIoTMQTTUnSubscribe
  (Connection: TsgcWSConnection; aPacketIdentifier: Word;
  aCodes: TsgcWSUNSUBACKS; UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
begin
  DoLog('#unsubscribed');
end;

procedure TFRMSGCClientIoT.AzureIoTConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected Socket');
end;

procedure TFRMSGCClientIoT.AzureIoTDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected Socket');
end;

procedure TFRMSGCClientIoT.AzureIoTMQTTConnect(Connection: TsgcWSConnection;
  const Session: Boolean; const ReasonCode: Integer; const ReasonName: string;
  const ConnectProperties: TsgcWSMQTTCONNACKProperties);
begin
  DoLog('#connected Azure IoT Broker');
end;

procedure TFRMSGCClientIoT.AzureIoTMQTTDisconnect(Connection: TsgcWSConnection;
  ReasonCode: Integer; const ReasonName: string;
  DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
begin
  DoLog('#disconnected Azure IoT Broker');
end;

procedure TFRMSGCClientIoT.AzureIoTMQTTPublish(Connection: TsgcWSConnection;
  aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
begin
  DoLog('Received Message: ' + aTopic + ' ' + aText);
end;

procedure TFRMSGCClientIoT.AzureIoTMQTTSubscribe(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
  SubscribeProperties: TsgcWSMQTTSUBACKProperties);
begin
  DoLog('#subscribed');
end;

procedure TFRMSGCClientIoT.AzureIoTMQTTUnSubscribe(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS;
  UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
begin
  DoLog('#unsubscribed');
end;

procedure TFRMSGCClientIoT.btnAmazonConnectClick(Sender: TObject);
begin
  AmazonIoT.Amazon.Endpoint := txtAmazonEndpoint.Text;
  AmazonIoT.Amazon.ClientId := txtAmazonClientId.Text;

  AmazonIoT.Certificate.Enabled := False;
  AmazonIoT.SignatureV4.Enabled := False;
  AmazonIoT.CustomAuthentication.Enabled := False;
  case cboAmazonAuthentication.ItemIndex of
    0:
      begin
        AmazonIoT.Certificate.Enabled := True;
        AmazonIoT.Certificate.CertFile := txtAmazonCertfile.Text;
        AmazonIoT.Certificate.KeyFile := txtAmazonKeyFile.Text;
      end;
    1:
      begin
        AmazonIoT.SignatureV4.Enabled := True;
        AmazonIoT.SignatureV4.Region := txtAmazonRegion.Text;
        AmazonIoT.SignatureV4.AccessKey := txtAmazonAccessKey.Text;
        AmazonIoT.SignatureV4.SecretKey := txtAmazonSecretKey.Text;
        AmazonIoT.SignatureV4.SessionToken := txtAmazonSessionToken.Text;
      end;
    2:
      begin
        AmazonIoT.CustomAuthentication.Enabled := True;
        AmazonIoT.CustomAuthentication.Parameters := txtAmazonParameters.Text;
        AmazonIoT.CustomAuthentication.Headers.Text := txtAmazonHeaders.Text;
        AmazonIoT.CustomAuthentication.WebSockets :=
          chkAmazonWebSockets.Checked;
      end;
  end;
  AmazonIoT.Active := True;
end;

procedure TFRMSGCClientIoT.btnAmazonDisconnectClick(Sender: TObject);
begin
  AmazonIoT.Active := False;
end;

procedure TFRMSGCClientIoT.btnAzureConnectClick(Sender: TObject);
begin
  DoInitialize;

  AzureIoT.Active := True;
end;

procedure TFRMSGCClientIoT.btnAzureDisconnectClick(Sender: TObject);
begin
  AzureIoT.Active := False;
end;

procedure TFRMSGCClientIoT.btnAzureFileUploadClick(Sender: TObject);
var
  oDialog: TOpenDialog;
begin
  DoInitialize;

  oDialog := TOpenDialog.Create(nil);
  Try
    if oDialog.Execute then
    begin
      AzureIoT.UploadFile(oDialog.FileName);
      DoLog('#upload file: ' + oDialog.FileName);
    end;
  Finally
    oDialog.Free;
  End;
end;

procedure TFRMSGCClientIoT.btnAzureSendDeviceToCloudClick(Sender: TObject);
begin
  case cboQoSAzure.ItemIndex of
    0:
      AzureIoT.Send_DeviceToCloud(txtPublishMessageAzure.Text, azuIoTQoS0);
    1:
      AzureIoT.Send_DeviceToCloud(txtPublishMessageAzure.Text, azuIoTQoS1);
  end;
end;

procedure TFRMSGCClientIoT.btnAzureSubscribeCloudToDeviceClick(Sender: TObject);
begin
  AzureIoT.Subscribe_CloudToDevice;
end;

procedure TFRMSGCClientIoT.btnAzureSubscribeDeviceTwinsClick(Sender: TObject);
begin
  AzureIoT.Subscribe_DeviceTwins;
end;

procedure TFRMSGCClientIoT.btnAzureUnsubscribeCloudToDeviceClick
  (Sender: TObject);
begin
  AzureIoT.UnSubscribe_CloudToDevice;
end;

procedure TFRMSGCClientIoT.btnAzureUnSubscribeDeviceTwinsClick(Sender: TObject);
begin
  AzureIoT.UnSubscribe_DeviceTwins;
end;

procedure TFRMSGCClientIoT.btnPublishAmazonClick(Sender: TObject);
begin
  case cboQoSAmazon.ItemIndex of
    0:
      AmazonIoT.Publish(txtPublishChannelAmazon.Text,
        txtPublishMessageAmazon.Text, awsIoTQoS0);
    1:
      AmazonIoT.Publish(txtPublishChannelAmazon.Text,
        txtPublishMessageAmazon.Text, awsIoTQoS1);
  end;
end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClick(Sender: TObject);
begin
  AmazonIoT.Subscribe(txtChannelAmazon.Text);
end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClientConnectedClick
  (Sender: TObject);
begin
  AmazonIoT.Subscribe_ClientConnected(txtAmazonClientIdEvents.Text);
end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClientDisconnectedClick
  (Sender: TObject);
begin
  AmazonIoT.Subscribe_ClientDisconnected(txtAmazonClientIdEvents.Text);
end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClientSubscribedClick
  (Sender: TObject);
begin
  AmazonIoT.Subscribe_ClientSubscribed(txtAmazonClientIdEvents.Text);
end;

procedure TFRMSGCClientIoT.btnSubscribeAmazonClientUnSubscribedClick
  (Sender: TObject);
begin
  AmazonIoT.Subscribe_ClientUnSubscribed(txtAmazonClientIdEvents.Text);
end;

procedure TFRMSGCClientIoT.btnUnsubscribeAmazonClick(Sender: TObject);
begin
  AmazonIoT.UnSubscribe(txtChannelAmazon.Text);
end;

procedure TFRMSGCClientIoT.btnAzureGetDeviceTwinsPropertiesClick
  (Sender: TObject);
begin
  AzureIoT.Get_DeviceTwinsProperties('GetDeviceTwinsProperties');
end;

procedure TFRMSGCClientIoT.btnAzureRespondPublicMethodClick(Sender: TObject);
begin
  AzureIoT.RespondPublicMethod(txtAzureRespondPublicMethodRequestId.Text,
    StrToInt(txtAzureRespondPublicMethodStatus.Text),
    txtAzureRespondPublicMethodText.Text);
end;

procedure TFRMSGCClientIoT.btnAzureSetDeviceTwinsPropertiesClick
  (Sender: TObject);
begin
  AzureIoT.Set_DeviceTwinsProperties('SetDeviceTwinsProperties',
    txtAzureSetDeviceTwinsProperties.Text);
end;

procedure TFRMSGCClientIoT.btnAzureSubscribeDirectMethodClick(Sender: TObject);
begin
  AzureIoT.Subscribe_DirectMethod;
end;

procedure TFRMSGCClientIoT.btnAzureUnSubscribeDirectMethodClick
  (Sender: TObject);
begin
  AzureIoT.UnSubscribe_DirectMethod;
end;

procedure TFRMSGCClientIoT.btnAzureProvisioningDeviceClientRegisterClick
  (Sender: TObject);
var
  oResponse: TsgcIoT_Azure_OperationRegistrationState;
begin
  DoInitialize;

  oResponse := TsgcIoT_Azure_OperationRegistrationState.Create;
  Try
    if AzureIoT.ProvisioningDeviceClient_Register
      (txtAzureProvisioningScopeId.Text,
      txtAzureProvisioningRegistrationId.Text, oResponse) then
      DoLog('#Provisioning Register OK: ' + oResponse.Status + ' Hub: ' +
        oResponse.AssignedHub + ' DeviceId: ' + oResponse.DeviceId)
    else
      DoLog('#Provisioning Register Error: ' + oResponse.Status);
  Finally
    FreeAndNil(oResponse);
  End;
end;

procedure TFRMSGCClientIoT.btnCreateCertificateFromCsrAmazonClick
  (Sender: TObject);
begin
  AmazonIoT.CreateCertificateFromCsr(txtCertificateSigningRequestAmazon.Text);
end;

procedure TFRMSGCClientIoT.btnCreateKeysAndCertificateAmazonClick(Sender:
    TObject);
begin
  AmazonIoT.CreateKeysAndCertificate;
end;

procedure TFRMSGCClientIoT.btnRegisterThingAmazonClick(Sender: TObject);
begin
  AmazonIoT.RegisterThing(txtRegisterThingTemplateAmazon.Text,
    Format('{"certificateOwnershipToken": "%s"}',
    [memoRegisterThingPayloadAmazon.Lines.Text]));
end;

procedure TFRMSGCClientIoT.btnSubscribeCreateCertificateFromCsrClick(Sender:
    TObject);
begin
  AmazonIoT.SubscribeCreateCertificateFromCsrResponse;
  AmazonIoT.SubscribeCreateCertificateFromCsrError;
end;

procedure TFRMSGCClientIoT.btnSubscribeCreateKeysAndCertificateAmazonClick(
    Sender: TObject);
begin
  AmazonIoT.SubscribeCreateKeysAndCertificateResponse;
  AmazonIoT.SubscribeCreateKeysAndCertificateError;
end;

procedure TFRMSGCClientIoT.btnSubscribeRegisterThingAmazonClick(Sender:
    TObject);
begin
  AmazonIoT.SubscribeRegisterThingResponse(txtRegisterThingTemplateAmazon.Text);
  AmazonIoT.SubscribeRegisterThingError(txtRegisterThingTemplateAmazon.Text);
end;

procedure TFRMSGCClientIoT.cboAmazonAuthenticationChange(Sender: TObject);
begin
  txtAmazonCertfile.Enabled := False;
  txtAmazonKeyFile.Enabled := False;
  txtAmazonRegion.Enabled := False;
  txtAmazonAccessKey.Enabled := False;
  txtAmazonSecretKey.Enabled := False;
  txtAmazonSessionToken.Enabled := False;
  txtAmazonParameters.Enabled := False;
  txtAmazonHeaders.Enabled := False;
  chkAmazonWebSockets.Enabled := False;

  case cboAmazonAuthentication.ItemIndex of
    0:
      begin
        txtAmazonCertfile.Enabled := True;
        txtAmazonKeyFile.Enabled := True;
      end;
    1:
      begin
        txtAmazonRegion.Enabled := True;
        txtAmazonAccessKey.Enabled := True;
        txtAmazonSecretKey.Enabled := True;
        txtAmazonSessionToken.Enabled := True;
      end;
    2:
      begin
        txtAmazonParameters.Enabled := True;
        txtAmazonHeaders.Enabled := True;
        chkAmazonWebSockets.Enabled := True;
      end;
  end;
end;

procedure TFRMSGCClientIoT.cboAzureAuthenticationChange(Sender: TObject);
begin
  AzureIoT.SAS.Enabled := False;
  AzureIoT.Certificate.Enabled := False;

  txtAzureSecretKey.Enabled := False;
  txtAzureCertfile.Enabled := False;
  txtAzureKeyFile.Enabled := False;

  case cboAzureAuthentication.ItemIndex of
    0:
      begin
        txtAzureSecretKey.Enabled := True;
        AzureIoT.SAS.Enabled := True;
      end;
    1:
      begin
        txtAzureCertfile.Enabled := True;
        txtAzureKeyFile.Enabled := True;
        AzureIoT.Certificate.Enabled := True;
      end;
  end;
end;

procedure TFRMSGCClientIoT.DoInitialize;
begin
  AzureIoT.Azure.IoTHub := txtAzureIoTHub.Text;
  AzureIoT.Azure.DeviceId := txtAzureDeviceId.Text;

  AzureIoT.Certificate.CertFile := txtAzureCertfile.Text;
  AzureIoT.Certificate.KeyFile := txtAzureKeyFile.Text;
  AzureIoT.Certificate.Password := '';

  AzureIoT.SAS.SecretKey := txtAzureSecretKey.Text;
  AzureIoT.SAS.KeyName := txtAzureKeyName.Text;
end;

procedure TFRMSGCClientIoT.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

