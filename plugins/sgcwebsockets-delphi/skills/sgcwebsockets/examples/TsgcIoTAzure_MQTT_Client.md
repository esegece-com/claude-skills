# TsgcIoTAzure_MQTT_Client - Example

Full source of `uAzureIOT.pas` from the **10.IoT_Clients/AzureWindowsService** demo, which uses `TsgcIoTAzure_MQTT_Client`.

API reference: [TsgcIoTAzure_MQTT_Client](../reference/api/TsgcIoTAzure_MQTT_Client.md)
Source demo: `10.IoT_Clients/AzureWindowsService` (file `uAzureIOT.pas`)

```pascal
unit uAzureIOT;

interface

uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Classes, Vcl.Graphics, Vcl.Controls, Vcl.SvcMgr, Vcl.Dialogs,
  sgcBase_Classes, sgcTCP_Classes, sgcIoT_Classes, sgcIoT_Client,
  sgcIoT_MQTT_Client, sgcIoT_Azure_MQTT_Client, sgcIoT, sgcWebSocket_Classes,
  sgcWebSocket_Protocol_MQTT_Message;

type
  TsgcAzureIoT = class(TService)
    azure: TsgcIoTAzure_MQTT_Client;
    procedure azureError(Connection: TsgcWSConnection; const Error: string);
    procedure azureException(Connection: TsgcWSConnection; E: Exception);
    procedure azureMQTTConnect(Connection: TsgcWSConnection; const Session:
        Boolean; const ReasonCode: Integer; const ReasonName: string; const
        ConnectProperties: TsgcWSMQTTCONNACKProperties);
    procedure azureMQTTDisconnect(Connection: TsgcWSConnection; ReasonCode:
        Integer; const ReasonName: string; DisconnectProperties:
        TsgcWSMQTTDISCONNECTProperties);
    procedure azureMQTTPublish(Connection: TsgcWSConnection; aTopic, aText: string;
        PublishProperties: TsgcWSMQTTPublishProperties);
    procedure azureMQTTSubscribe(Connection: TsgcWSConnection; aPacketIdentifier:
        Word; aCodes: TsgcWSSUBACKS; SubscribeProperties:
        TsgcWSMQTTSUBACKProperties);
    procedure azureMQTTUnSubscribe(Connection: TsgcWSConnection; aPacketIdentifier:
        Word; aCodes: TsgcWSUNSUBACKS; UnsubscribeProperties:
        TsgcWSMQTTUNSUBACKProperties);
    procedure ServiceExecute(Sender: TService);
    procedure ServiceStart(Sender: TService; var Started: Boolean);
    procedure ServiceStop(Sender: TService; var Stopped: Boolean);
  private
    FLog: TStringList;
  public
    procedure DoLog(const aText: String);
    function GetServiceController: TServiceController; override;
    { Public declarations }
  end;

var
  sgcAzureIoT: TsgcAzureIoT;

implementation

uses
  INIFiles;

{$R *.dfm}

procedure ServiceController(CtrlCode: DWord); stdcall;
begin
  sgcAzureIoT.Controller(CtrlCode);
end;

procedure TsgcAzureIoT.azureError(Connection: TsgcWSConnection; const Error:
    string);
begin
  DoLog('Error: ' + Error);
end;

procedure TsgcAzureIoT.azureException(Connection: TsgcWSConnection; E:
    Exception);
begin
  DoLog('Exception: ' + E.Message);
end;

procedure TsgcAzureIoT.azureMQTTConnect(Connection: TsgcWSConnection; const
    Session: Boolean; const ReasonCode: Integer; const ReasonName: string;
    const ConnectProperties: TsgcWSMQTTCONNACKProperties);
begin
  DoLog('Connected');

  azure.Subscribe_CloudToDevice;
end;

procedure TsgcAzureIoT.azureMQTTDisconnect(Connection: TsgcWSConnection;
    ReasonCode: Integer; const ReasonName: string; DisconnectProperties:
    TsgcWSMQTTDISCONNECTProperties);
begin
  DoLog('Disconnected');
end;

procedure TsgcAzureIoT.azureMQTTPublish(Connection: TsgcWSConnection; aTopic,
    aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
begin
  DoLog('Message Received: ' + aText);
end;

procedure TsgcAzureIoT.azureMQTTSubscribe(Connection: TsgcWSConnection;
    aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS; SubscribeProperties:
    TsgcWSMQTTSUBACKProperties);
begin
  DoLog('Subscribed');
end;

procedure TsgcAzureIoT.azureMQTTUnSubscribe(Connection: TsgcWSConnection;
    aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS; UnsubscribeProperties:
    TsgcWSMQTTUNSUBACKProperties);
begin
  DoLog('UnSubscribed');
end;

procedure TsgcAzureIoT.DoLog(const aText: String);
begin
  if Assigned(FLog) then
  begin
    FLog.Add(FormatDateTime('yyyy-mm-dd hh:nn:ss zzz', Now) + ' ' + aText);
    FLog.SaveToFile(ChangeFileExt(ParamStr(0), '.log'));
  end;
end;

function TsgcAzureIoT.GetServiceController: TServiceController;
begin
  Result := ServiceController;
end;

procedure TsgcAzureIoT.ServiceExecute(Sender: TService);
begin
  while not Terminated do
  begin
    ServiceThread.ProcessRequests(false);
    TThread.Sleep(1000);
  end;
end;

procedure TsgcAzureIoT.ServiceStart(Sender: TService; var Started: Boolean);
var
  oINI: TINIFile;
begin
  FLog := TStringList.Create;
  oINI := TINIFile.Create(ChangeFileExt(ParamStr(0), '.ini'));
  Try
    azure.Azure.IoTHub := oINI.ReadString('Azure', 'IoTHub', '');
    azure.Azure.DeviceId := oINI.ReadString('Azure', 'DeviceId', '');
    azure.SAS.Enabled := True;
    azure.SAS.SecretKey := oINI.ReadString('Azure', 'SecretKey', '');
  Finally
    oINI.Free;
  End;
  azure.Active := True;
end;

procedure TsgcAzureIoT.ServiceStop(Sender: TService; var Stopped: Boolean);
begin
  azure.Active := False;
  FreeAndNil(FLog);
end;

end.
```

