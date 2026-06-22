# TsgcHTTPAWS_SQS_Client - Example

Full source of `FAmazonSQS.pas` from the **20.HTTP_Protocol/04.AWS/01.Amazon_SQS** demo, which uses `TsgcHTTPAWS_SQS_Client`.

API reference: [TsgcHTTPAWS_SQS_Client](../reference/api/TsgcHTTPAWS_SQS_Client.md)
Source demo: `20.HTTP_Protocol/04.AWS/01.Amazon_SQS` (file `FAmazonSQS.pas`)

```pascal
unit FAmazonSQS;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcBase_Classes, sgcHTTP_Amazon_AWS, sgcHTTP_Amazon_SQS, sgcHTTP,
  StdCtrls, ExtCtrls;

type
  TFRMAmazonSQS = class(TForm)
    pnlTop: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    txtRegion: TEdit;
    txtAccessKey: TEdit;
    txtSecretKey: TEdit;
    pnlSQS: TPanel;
    btnCreateQueue: TButton;
    btnDeleteQueue: TButton;
    memoLog: TMemo;
    SQS: TsgcHTTPAWS_SQS_Client;
    txtQueueName: TEdit;
    Label4: TLabel;
    btnGetQueueAttributes: TButton;
    txtVisibilityTimeout: TEdit;
    Label5: TLabel;
    btnSetQueueAttributes: TButton;
    btnListQueues: TButton;
    Label6: TLabel;
    txtMessageBody: TEdit;
    btnSendMessage: TButton;
    btnReceiveMessage: TButton;
    txtReceiptHandle: TEdit;
    Label7: TLabel;
    btnDeleteMessage: TButton;
    btnPurgueQueue: TButton;
    procedure btnCreateQueueClick(Sender: TObject);
    procedure btnDeleteMessageClick(Sender: TObject);
    procedure btnDeleteQueueClick(Sender: TObject);
    procedure btnGetQueueAttributesClick(Sender: TObject);
    procedure btnListQueuesClick(Sender: TObject);
    procedure btnPurgueQueueClick(Sender: TObject);
    procedure btnReceiveMessageClick(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure btnSetQueueAttributesClick(Sender: TObject);
    procedure SQSSQSError(Sender: TObject; const Error_Code, Error_Description,
      RawError: string);
  private
    procedure DoLog(const aText: String);
    procedure DoSQSConfig;
  public
    procedure ListQueues;
  public
    procedure CreateQueue;
    procedure DeleteQueue;
    procedure GetQueueAttributes;
    procedure SetQueueAttributes;
  public
    procedure SendMessage;
    procedure ReceiveMessage;
    procedure DeleteMessage;
    procedure PurgueQueue;
  end;

var
  FRMAmazonSQS: TFRMAmazonSQS;

implementation

{$R *.dfm}

procedure TFRMAmazonSQS.btnCreateQueueClick(Sender: TObject);
begin
  CreateQueue;
end;

procedure TFRMAmazonSQS.btnDeleteMessageClick(Sender: TObject);
begin
  DeleteMessage;
end;

procedure TFRMAmazonSQS.btnDeleteQueueClick(Sender: TObject);
begin
  DeleteQueue;
end;

procedure TFRMAmazonSQS.btnGetQueueAttributesClick(Sender: TObject);
begin
  GetQueueAttributes;
end;

procedure TFRMAmazonSQS.btnListQueuesClick(Sender: TObject);
begin
  ListQueues;
end;

procedure TFRMAmazonSQS.btnPurgueQueueClick(Sender: TObject);
begin
  PurgueQueue;
end;

procedure TFRMAmazonSQS.btnReceiveMessageClick(Sender: TObject);
begin
  ReceiveMessage;
end;

procedure TFRMAmazonSQS.btnSendMessageClick(Sender: TObject);
begin
  SendMessage;
end;

procedure TFRMAmazonSQS.btnSetQueueAttributesClick(Sender: TObject);
begin
  SetQueueAttributes;
end;

procedure TFRMAmazonSQS.CreateQueue;
var
  vURL: string;
begin
  DoSQSConfig;

  vURL := SQS.CreateQueue(txtQueueName.Text);
  if vURL <> '' then
    DoLog('#CreateQueue: ' + vURL);
end;

procedure TFRMAmazonSQS.DeleteMessage;
begin
  DoSQSConfig;

  if SQS.DeleteMessage(txtQueueName.Text, txtReceiptHandle.Text) then
  begin
    DoLog('#DeleteMessage: ok');
    txtReceiptHandle.Text := '';
  end
  else
    DoLog('#DeleteMessage: error');
end;

procedure TFRMAmazonSQS.DeleteQueue;
begin
  DoSQSConfig;

  if SQS.DeleteQueue(txtQueueName.Text) then
    DoLog('#Delete Queue: ok')
  else
    DoLog('#Delete Queue: error');
end;

procedure TFRMAmazonSQS.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMAmazonSQS.DoSQSConfig;
begin
  SQS.AWSOptions.Region := txtRegion.Text;
  SQS.AWSOptions.AccessKey := txtAccessKey.Text;
  SQS.AWSOptions.SecretKey := txtSecretKey.Text;
end;

procedure TFRMAmazonSQS.GetQueueAttributes;
var
  i: Integer;
  oAttributes: TsgcSQSAttributes;
begin
  DoSQSConfig;

  oAttributes := TsgcSQSAttributes.Create;
  Try
    if SQS.GetQueueAttributes(txtQueueName.Text, oAttributes) then
    begin
      for i := 0 to oAttributes.Count - 1 do
        DoLog('#Attribute: ' + TsgcSQSAttribute(oAttributes.Item[i])
          .AttributeName + ' ' + TsgcSQSAttribute(oAttributes.Item[i])
          .AttributeValue);
    end
    else
      DoLog('#GetQueueAttributes: error');
  Finally
    FreeAndNil(oAttributes);
  End;
end;

procedure TFRMAmazonSQS.ListQueues;
var
  oList: TStringList;
begin
  DoSQSConfig;

  oList := TStringList.Create;
  Try
    if SQS.ListQueues(oList) then
      DoLog('#ListQueues: ' + oList.text)
    else
      DoLog('#ListQueues: error');
  Finally
    FreeAndNil(oList);
  End;
end;

procedure TFRMAmazonSQS.PurgueQueue;
begin
  DoSQSConfig;

  if SQS.PurgueQueue(txtQueueName.Text) then
    DoLog('#PurgueQueue: ok')
  else
    DoLog('#PurgueQueue: error');
end;

procedure TFRMAmazonSQS.ReceiveMessage;
var
  i: Integer;
  oResponses: TsgcSQSReceiveMessageResponses;
begin
  DoSQSConfig;

  oResponses := TsgcSQSReceiveMessageResponses.Create;
  Try
    if SQS.ReceiveMessage(txtQueueName.Text, oResponses) then
    begin
      for i := 0 to oResponses.Count - 1 do
      begin
        DoLog('#ReceiveMessage: ' + TsgcSQSReceiveMessageResponse(oResponses.Item[i]).Body);
        txtReceiptHandle.Text := TsgcSQSReceiveMessageResponse(oResponses.Item[i]).ReceiptHandle;
      end;
    end;
  Finally
    FreeAndNil(oResponses);
  End;
end;

procedure TFRMAmazonSQS.SendMessage;
begin
  DoSQSConfig;

  if SQS.SendMessage(txtQueueName.Text, txtMessageBody.Text) then
    DoLog('#SendMessage: ok')
  else
    DoLog('#SendMessage: error');
end;

procedure TFRMAmazonSQS.SetQueueAttributes;
var
  oAttributes: TsgcSQSAttributes;
begin
  DoSQSConfig;

  oAttributes := TsgcSQSAttributes.Create;
  Try
    oAttributes.AddSQSAttribute(sqsatVisibilityTimeout, txtVisibilityTimeout.Text);

    if SQS.SetQueueAttributes(txtQueueName.Text, oAttributes) then
      DoLog('#SetQueueAttributes: ok')
    else
      DoLog('#SetQueueAttributes: error');
  Finally
    FreeAndNil(oAttributes);
  End;
end;

procedure TFRMAmazonSQS.SQSSQSError(Sender: TObject;
  const Error_Code, Error_Description, RawError: string);
begin
  DoLog('#Error: ' + Error_Code + ' ' + Error_Description);
end;

end.
```

