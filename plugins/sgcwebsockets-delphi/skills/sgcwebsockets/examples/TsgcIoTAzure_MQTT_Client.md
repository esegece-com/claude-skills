# TsgcIoTAzure_MQTT_Client - Example

Usage of `TsgcIoTAzure_MQTT_Client` extracted from the **10.IoT_Clients/AzureWindowsService** demo. See the full project for context.

API reference: [TsgcIoTAzure_MQTT_Client](../reference/api/TsgcIoTAzure_MQTT_Client.md)
Source demo: `10.IoT_Clients/AzureWindowsService` (file `uAzureIOT.pas`)

```pascal
procedure TsgcAzureIoT.azureMQTTConnect(Connection: TsgcWSConnection; const
  Session: Boolean; const ReasonCode: Integer; const ReasonName: string;
  const ConnectProperties: TsgcWSMQTTCONNACKProperties);
  begin
  DoLog('Connected');
  
  azure.Subscribe_CloudToDevice;
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
procedure TsgcAzureIoT.ServiceStop(Sender: TService; var Stopped: Boolean);
  begin
  azure.Active := False;
  FreeAndNil(FLog);
  end;

```

