# TsgcWSPClient_Files - Example

Full source of `fClientFiles.pas` from the **02.WebSocket_Protocols/02.Send_Receive_Files_Protocol** demo, which uses `TsgcWSPClient_Files`.

API reference: [TsgcWSPClient_Files](../reference/api/TsgcWSPClient_Files.md)
Source demo: `02.WebSocket_Protocols/02.Send_Receive_Files_Protocol` (file `fClientFiles.pas`)

```pascal
unit fClientFiles;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ComCtrls, StdCtrls, ExtCtrls,
  // sgcWebSockets
  sgcWebSocket_Classes,
  sgcWebSocket_Server, sgcWebSocket, sgcWebSocket_Protocol_Base_Server,
  sgcWebSocket_Protocol_Files_Server, sgcWebSocket_Protocols,
  sgcWebSocket_Types, sgcWebSocket_Protocol_Files_Message,
  sgcWebSocket_Protocol_Base_Client, sgcWebSocket_Protocol_Files_Client,
  sgcWebSocket_Client, sgcBase_Classes, sgcTCP_Classes,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Helpers;

type
  TFRMClientFiles = class(TForm)
    pnlLeft: TPanel;
    pnlRight: TPanel;
    pnlBody: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    btnSend: TButton;
    trackSize: TTrackBar;
    cboQoS: TComboBox;
    memoLog: TMemo;
    progFileSent: TProgressBar;
    lblFileSent: TLabel;
    lblFileReceived: TLabel;
    progFileReceived: TProgressBar;
    txtSaveDirectory: TEdit;
    btnSaveDirectory: TButton;
    pnlTop: TPanel;
    txtHost: TEdit;
    btnStart: TButton;
    txtPort: TEdit;
    btnStop: TButton;
    Label5: TLabel;
    Label6: TLabel;
    Label7: TLabel;
    client: TsgcWebSocketClient;
    client_files: TsgcWSPClient_Files;
    btnSubscribe: TButton;
    procedure btnSaveDirectoryClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnSubscribeClick(Sender: TObject);
    procedure client_filesConnect(Connection: TsgcWSConnection);
    procedure client_filesDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure client_filesFileReceived(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile);
    procedure client_filesFileReceivedError(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; const Error: string);
    procedure client_filesFileReceivedFragment(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; var Cancel: Boolean);
    procedure client_filesFileSent(Connection: TsgcWSConnection; const aMessage:
        TsgcWSMessageFile);
    procedure client_filesFileSentAcknowledgment(Connection: TsgcWSConnection;
        const aMessage: TsgcWSMessageFile);
    procedure client_filesFileSentError(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; const Error: string);
    procedure client_filesFileSentFragmentRequest(const aMessage:
        TsgcWSMessageFile; var Cancel: Boolean);
  private
    FMessage: TsgcWSMessageFile;
    procedure DoFileSentFragment;
    procedure DoFileReceivedFragment;
    procedure DoSendFile;
    procedure DoStart;
    procedure DoStop;
    procedure DoSyncLog(const aText: String);
  end;

var
  FRMClientFiles: TFRMClientFiles;

implementation

{$R *.dfm}

procedure TFRMClientFiles.btnSaveDirectoryClick(Sender: TObject);
var
  oDialog: TSaveDialog;
begin
  oDialog := TSaveDialog.Create(nil);
  Try
    if oDialog.Execute then
      txtSaveDirectory.Text := ExtractFilePath(oDialog.FileName);
  Finally
    FreeAndNil(oDialog);
  End;
end;

procedure TFRMClientFiles.btnSendClick(Sender: TObject);
begin
  DoSendFile;
end;

procedure TFRMClientFiles.btnStartClick(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMClientFiles.btnStopClick(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMClientFiles.btnSubscribeClick(Sender: TObject);
begin
  client_files.Subscribe('test');
end;

procedure TFRMClientFiles.DoFileReceivedFragment;
begin
  lblFileReceived.Caption := FMessage.FileName + ' ' + IntToStr(FMessage.FilePosition);

  progFileReceived.Position := FMessage.FilePosition;
  progFileReceived.Max := FMessage.FileSize;
end;

procedure TFRMClientFiles.DoFileSentFragment;
begin
  lblFileSent.Caption := FMessage.FileName + ' ' + IntToStr(FMessage.FilePosition);

  progFileSent.Position := FMessage.FilePosition;
  progFileSent.Max := FMessage.FileSize;
end;

procedure TFRMClientFiles.DoSendFile;
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    if oDialog.Execute then
      client_files.SendFile(oDialog.FileName);
  Finally
    FreeAndNil(oDialog);
  End;
end;

procedure TFRMClientFiles.DoStart;
begin
  client_files.Files.BufferSize := TrackSize.Position;
  client_files.Files.QoS.Level := TwsQoS(Ord(cboQoS.ItemIndex));
  client_files.Files.SaveDirectory := txtSaveDirectory.Text;

  client.Host := txtHost.Text;
  client.Port := StrToInt(txtPort.Text);

  client.NotifyEvents := neNoSync;
  client.Active := True;
end;

procedure TFRMClientFiles.DoStop;
begin
  Client.Active := False;
end;

procedure TFRMClientFiles.DoSyncLog(const aText: String);
begin
  TThread.Queue(nil,
    procedure
    begin;
      memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ': ' + aText);
    end);
end;

procedure TFRMClientFiles.client_filesConnect(Connection: TsgcWSConnection);
begin
  DoSyncLog('Connected: ' + Connection.Guid);
end;

procedure TFRMClientFiles.client_filesDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  DoSyncLog('Disconnected: ' + Connection.Guid);
end;

procedure TFRMClientFiles.client_filesFileReceived(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('File ' + aMessage.FileName + ' has been received successfully.');
end;

procedure TFRMClientFiles.client_filesFileReceivedError(Connection: TsgcWSConnection;
    const aMessage: TsgcWSMessageFile; const Error: string);
begin
  DoSyncLog('File Received Error ' + aMessage.FileName + ': ' + Error);
end;

procedure TFRMClientFiles.client_filesFileReceivedFragment(Connection: TsgcWSConnection;
    const aMessage: TsgcWSMessageFile; var Cancel: Boolean);
begin
  FMessage := aMessage;

  NotifyMethod(DoFileReceivedFragment);
end;

procedure TFRMClientFiles.client_filesFileSent(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('File ' + aMessage.FileName + ' has been sent successfully.');
end;

procedure TFRMClientFiles.client_filesFileSentAcknowledgment(Connection:
    TsgcWSConnection; const aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('Received Acknowledgment ' + aMessage.Id);
end;

procedure TFRMClientFiles.client_filesFileSentError(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile; const Error: string);
begin
  DoSyncLog('File Sent Error ' + aMessage.FileName + ': ' + Error);
end;

procedure TFRMClientFiles.client_filesFileSentFragmentRequest(const aMessage:
    TsgcWSMessageFile; var Cancel: Boolean);
begin
  FMessage := aMessage;

  NotifyMethod(DoFileSentFragment);
end;

end.
```

