# TsgcWSPClient_Kafka - Example

Full source of `fKafka.pas` from the **02.WebSocket_Protocols/13.Kafka** demo, which uses `TsgcWSPClient_Kafka`.

API reference: [TsgcWSPClient_Kafka](../reference/api/TsgcWSPClient_Kafka.md)
Source demo: `02.WebSocket_Protocols/13.Kafka` (file `fKafka.pas`)

```pascal
{ ***************************************************************************
  sgcWebSocket component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fKafka;

{$I sgcVer.inc}

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, ExtCtrls, ComCtrls, StdCtrls,
  // sgc
  sgcWebSocket, sgcWebSocket_Protocols, sgcKafka_Classes;

type
  TfrmKafka = class(TForm)
    pnlTop: TPanel;
    lblHost: TLabel;
    txtHost: TEdit;
    lblPort: TLabel;
    txtPort: TEdit;
    lblClientId: TLabel;
    txtClientId: TEdit;
    lblSaslUsername: TLabel;
    txtSaslUsername: TEdit;
    lblSaslPassword: TLabel;
    txtSaslPassword: TEdit;
    btnConnect: TButton;
    btnDisconnect: TButton;
    PageControl1: TPageControl;
    tabProducer: TTabSheet;
    lblProdTopic: TLabel;
    txtProdTopic: TEdit;
    lblProdKey: TLabel;
    txtProdKey: TEdit;
    lblProdValue: TLabel;
    txtProdValue: TEdit;
    lblProdPartition: TLabel;
    txtProdPartition: TEdit;
    btnProduce: TButton;
    tabConsumer: TTabSheet;
    lblConsTopic: TLabel;
    txtConsTopic: TEdit;
    lblConsGroupId: TLabel;
    txtConsGroupId: TEdit;
    lblPollTimeout: TLabel;
    txtPollTimeout: TEdit;
    btnSubscribe: TButton;
    btnUnsubscribe: TButton;
    btnPoll: TButton;
    tabAdmin: TTabSheet;
    lblAdminTopic: TLabel;
    txtAdminTopic: TEdit;
    lblAdminPartitions: TLabel;
    txtAdminPartitions: TEdit;
    lblAdminReplication: TLabel;
    txtAdminReplication: TEdit;
    btnCreateTopic: TButton;
    btnDeleteTopic: TButton;
    btnGetMetadata: TButton;
    btnListGroups: TButton;
    tabOffsets: TTabSheet;
    lblOffsetTopic: TLabel;
    txtOffsetTopic: TEdit;
    lblOffsetPartition: TLabel;
    txtOffsetPartition: TEdit;
    btnGetLatest: TButton;
    btnGetEarliest: TButton;
    btnGetCommitted: TButton;
    btnCommit: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnProduceClick(Sender: TObject);
    procedure btnSubscribeClick(Sender: TObject);
    procedure btnUnsubscribeClick(Sender: TObject);
    procedure btnPollClick(Sender: TObject);
    procedure btnCreateTopicClick(Sender: TObject);
    procedure btnDeleteTopicClick(Sender: TObject);
    procedure btnGetMetadataClick(Sender: TObject);
    procedure btnListGroupsClick(Sender: TObject);
    procedure btnGetLatestClick(Sender: TObject);
    procedure btnGetEarliestClick(Sender: TObject);
    procedure btnGetCommittedClick(Sender: TObject);
    procedure btnCommitClick(Sender: TObject);
  private
    fWSClient: TsgcWebSocketClient;
    fKafkaProtocol: TsgcWSPClient_Kafka;
    function GetWSClient: TsgcWebSocketClient;
    function GetKafkaProtocol: TsgcWSPClient_Kafka;
    procedure DoLog(const aText: string);
    procedure DoLoadSettings;
    procedure DoSaveSettings;
    procedure OnKafkaMessage(Sender: TObject; const aMessage: TsgcKafkaMessage);
    procedure OnKafkaError(Sender: TObject; const aErrorCode: Integer;
      const aErrorMessage: string);
    procedure OnKafkaConnect(Sender: TObject);
    procedure OnKafkaDisconnect(Sender: TObject; const aCode: Integer);
    procedure OnKafkaProduce(Sender: TObject; const aTopic: string;
      aPartition: Integer; aOffset: Int64; aErrorCode: SmallInt);
  public
    property WSClient: TsgcWebSocketClient read GetWSClient;
    property KafkaProtocol: TsgcWSPClient_Kafka read GetKafkaProtocol;
  end;

var
  frmKafka: TfrmKafka;

implementation

{$R *.dfm}

uses
  INIFiles;

procedure TfrmKafka.FormCreate(Sender: TObject);
begin
  DoLoadSettings;
end;

procedure TfrmKafka.FormDestroy(Sender: TObject);
begin
  DoSaveSettings;
end;

function TfrmKafka.GetWSClient: TsgcWebSocketClient;
begin
  if not Assigned(fWSClient) then
  begin
    fWSClient := TsgcWebSocketClient.Create(Self);
    fWSClient.Specifications.RFC6455 := False;
  end;
  Result := fWSClient;
end;

function TfrmKafka.GetKafkaProtocol: TsgcWSPClient_Kafka;
begin
  if not Assigned(fKafkaProtocol) then
  begin
    fKafkaProtocol := TsgcWSPClient_Kafka.Create(Self);
    fKafkaProtocol.Client := WSClient;
    fKafkaProtocol.OnKafkaMessage := OnKafkaMessage;
    fKafkaProtocol.OnKafkaError := OnKafkaError;
    fKafkaProtocol.OnKafkaConnect := OnKafkaConnect;
    fKafkaProtocol.OnKafkaDisconnect := OnKafkaDisconnect;
    fKafkaProtocol.OnKafkaProduce := OnKafkaProduce;
  end;
  Result := fKafkaProtocol;
end;

procedure TfrmKafka.DoLog(const aText: string);
begin
  if Assigned(memoLog) then
  begin
    memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aText);
  end;
end;

procedure TfrmKafka.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtHost.Text := oINI.ReadString('KAFKA', 'HOST', 'localhost');
    txtPort.Text := oINI.ReadString('KAFKA', 'PORT', '9092');
    txtClientId.Text := oINI.ReadString('KAFKA', 'CLIENT_ID',
      'sgc-kafka-client');
    txtSaslUsername.Text := oINI.ReadString('KAFKA', 'SASL_USERNAME', '');
    txtSaslPassword.Text := oINI.ReadString('KAFKA', 'SASL_PASSWORD', '');
  Finally
    oINI.Free;
  End;
end;

procedure TfrmKafka.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('KAFKA', 'HOST', txtHost.Text);
    oINI.WriteString('KAFKA', 'PORT', txtPort.Text);
    oINI.WriteString('KAFKA', 'CLIENT_ID', txtClientId.Text);
    oINI.WriteString('KAFKA', 'SASL_USERNAME', txtSaslUsername.Text);
    oINI.WriteString('KAFKA', 'SASL_PASSWORD', txtSaslPassword.Text);
  Finally
    oINI.Free;
  End;
end;

{ Connection }

procedure TfrmKafka.btnConnectClick(Sender: TObject);
begin
  WSClient.Host := txtHost.Text;
  WSClient.Port := StrToIntDef(txtPort.Text, 9092);
  KafkaProtocol.KafkaOptions.ClientId := txtClientId.Text;
  { TODO: SASL settings are not yet exposed on the protocol adapter }
  Try
    DoLog('Connecting to ' + txtHost.Text + ':' + txtPort.Text);
    WSClient.Active := True;
  Except
    on E: Exception do
      DoLog('Connect error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnDisconnectClick(Sender: TObject);
begin
  Try
    WSClient.Active := False;
    DoLog('Disconnected');
  Except
    on E: Exception do
      DoLog('Disconnect error: ' + E.Message);
  End;
end;

{ Producer }

procedure TfrmKafka.btnProduceClick(Sender: TObject);
begin
  Try
    KafkaProtocol.Produce(txtProdTopic.Text, txtProdValue.Text, txtProdKey.Text,
      StrToIntDef(txtProdPartition.Text, 0));
  Except
    on E: Exception do
      DoLog('Produce error: ' + E.Message);
  End;
end;

{ Consumer }

procedure TfrmKafka.btnSubscribeClick(Sender: TObject);
begin
  KafkaProtocol.KafkaOptions.Consumer.GroupId := txtConsGroupId.Text;
  { start a new group from the beginning so existing messages are received }
  KafkaProtocol.KafkaOptions.Consumer.OffsetReset := kafkaOffsetEarliest;
  Try
    KafkaProtocol.Subscribe([txtConsTopic.Text]);
    DoLog('Subscribed to: ' + txtConsTopic.Text);
  Except
    on E: Exception do
      DoLog('Subscribe error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnUnsubscribeClick(Sender: TObject);
begin
  Try
    KafkaProtocol.Unsubscribe;
    DoLog('Unsubscribed');
  Except
    on E: Exception do
      DoLog('Unsubscribe error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnPollClick(Sender: TObject);
var
  oMessages: TsgcKafkaMessages;
  i: Integer;
begin
  Try
    oMessages := KafkaProtocol.Poll(StrToIntDef(txtPollTimeout.Text, 1000));
    Try
      DoLog(Format('Fetched %d messages', [oMessages.Count]));
      for i := 0 to oMessages.Count - 1 do
        DoLog(Format('  [%s:%d@%d] key=%s value=%s', [oMessages[i].Topic,
          oMessages[i].Partition, oMessages[i].Offset,
          oMessages[i].GetKeyString, oMessages[i].GetValueString]));
    Finally
      oMessages.Free;
    End;
  Except
    on E: Exception do
      DoLog('Poll error: ' + E.Message);
  End;
end;

{ Admin }

procedure TfrmKafka.btnCreateTopicClick(Sender: TObject);
begin
  Try
    KafkaProtocol.CreateTopic(txtAdminTopic.Text,
      StrToIntDef(txtAdminPartitions.Text, 1),
      StrToIntDef(txtAdminReplication.Text, 1));
    DoLog('Topic created: ' + txtAdminTopic.Text);
  Except
    on E: Exception do
      DoLog('CreateTopic error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnDeleteTopicClick(Sender: TObject);
begin
  Try
    KafkaProtocol.DeleteTopic(txtAdminTopic.Text);
    DoLog('Topic deleted: ' + txtAdminTopic.Text);
  Except
    on E: Exception do
      DoLog('DeleteTopic error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnGetMetadataClick(Sender: TObject);
var
  oMetadata: TsgcKafkaMetadataResponse;
  i: Integer;
  vTopics: string;
begin
  Try
    oMetadata := KafkaProtocol.GetMetadata([txtAdminTopic.Text]);
    Try
      vTopics := '';
      for i := 0 to Length(oMetadata.Topics) - 1 do
      begin
        if vTopics <> '' then
          vTopics := vTopics + ', ';
        vTopics := vTopics + oMetadata.Topics[i].Name;
      end;
      DoLog(Format('Metadata: %d brokers, topics: %s',
        [Length(oMetadata.Brokers), vTopics]));
    Finally
      oMetadata.Free;
    End;
  Except
    on E: Exception do
      DoLog('GetMetadata error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnListGroupsClick(Sender: TObject);
var
  oGroups: TsgcKafkaListGroupsResponse;
  i: Integer;
  vGroupIds: string;
begin
  Try
    oGroups := KafkaProtocol.ListGroups;
    vGroupIds := '';
    for i := 0 to Length(oGroups.Groups) - 1 do
    begin
      if vGroupIds <> '' then
        vGroupIds := vGroupIds + ', ';
      vGroupIds := vGroupIds + oGroups.Groups[i].GroupId;
    end;
    DoLog(Format('Groups: %s', [vGroupIds]));
  Except
    on E: Exception do
      DoLog('ListGroups error: ' + E.Message);
  End;
end;

{ Offsets }

procedure TfrmKafka.btnGetLatestClick(Sender: TObject);
begin
  Try
    DoLog(Format('Latest offset: %d',
      [KafkaProtocol.GetLatestOffset(txtOffsetTopic.Text,
      StrToIntDef(txtOffsetPartition.Text, 0))]));
  Except
    on E: Exception do
      DoLog('GetLatestOffset error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnGetEarliestClick(Sender: TObject);
begin
  Try
    DoLog(Format('Earliest offset: %d',
      [KafkaProtocol.GetEarliestOffset(txtOffsetTopic.Text,
      StrToIntDef(txtOffsetPartition.Text, 0))]));
  Except
    on E: Exception do
      DoLog('GetEarliestOffset error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnGetCommittedClick(Sender: TObject);
begin
  Try
    DoLog(Format('Committed offset: %d',
      [KafkaProtocol.GetCommittedOffset(txtOffsetTopic.Text,
      StrToIntDef(txtOffsetPartition.Text, 0))]));
  Except
    on E: Exception do
      DoLog('GetCommittedOffset error: ' + E.Message);
  End;
end;

procedure TfrmKafka.btnCommitClick(Sender: TObject);
begin
  Try
    KafkaProtocol.CommitSync;
    DoLog('Offsets committed');
  Except
    on E: Exception do
      DoLog('CommitSync error: ' + E.Message);
  End;
end;

{ Events }

procedure TfrmKafka.OnKafkaMessage(Sender: TObject;
  const aMessage: TsgcKafkaMessage);
begin
  DoLog(Format('Message: [%s:%d@%d] %s', [aMessage.Topic, aMessage.Partition,
    aMessage.Offset, aMessage.GetValueString]));
end;

procedure TfrmKafka.OnKafkaError(Sender: TObject; const aErrorCode: Integer;
  const aErrorMessage: string);
begin
  DoLog(Format('Error %d: %s', [aErrorCode, aErrorMessage]));
end;

procedure TfrmKafka.OnKafkaConnect(Sender: TObject);
begin
  DoLog('Kafka connected');
end;

procedure TfrmKafka.OnKafkaDisconnect(Sender: TObject; const aCode: Integer);
begin
  DoLog(Format('Kafka disconnected (code: %d)', [aCode]));
end;

procedure TfrmKafka.OnKafkaProduce(Sender: TObject; const aTopic: string;
  aPartition: Integer; aOffset: Int64; aErrorCode: SmallInt);
begin
  if aErrorCode = 0 then
    DoLog(Format('Produced to %s:%d at offset %d', [aTopic, aPartition,
      aOffset]))
  else
    DoLog(Format('Produce error %d for %s:%d', [aErrorCode, aTopic,
      aPartition]));
end;

end.
```

