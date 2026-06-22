# TsgcWSPServer_Files - Example

Full source of `fServerFiles.pas` from the **02.WebSocket_Protocols/02.Send_Receive_Files_Protocol** demo, which uses `TsgcWSPServer_Files`.

API reference: [TsgcWSPServer_Files](../reference/api/TsgcWSPServer_Files.md)
Source demo: `02.WebSocket_Protocols/02.Send_Receive_Files_Protocol` (file `fServerFiles.pas`)

```pascal
unit fServerFiles;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ComCtrls, StdCtrls, ExtCtrls,
  // sgcWebSockets
  sgcWebSocket_Classes, sgcWebSocket_Helpers,
  sgcWebSocket_Server, sgcWebSocket, sgcWebSocket_Protocol_Base_Server,
  sgcWebSocket_Protocol_Files_Server, sgcWebSocket_Protocols,
  sgcWebSocket_Types, sgcWebSocket_Protocol_Files_Message,
  sgcWebSocket_Classes_Indy, sgcBase_Classes, sgcTCP_Classes;

type
  TForm6 = class(TForm)
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
    server_files: TsgcWSPServer_Files;
    server: TsgcWebSocketServer;
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
    btnBroadcast: TButton;
    lblFileSent: TLabel;
    procedure btnBroadcastClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnSaveDirectoryClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure server_filesConnect(Connection: TsgcWSConnection);
    procedure server_filesDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure server_filesFileReceived(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile);
    procedure server_filesFileReceivedError(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; const Error: string);
    procedure server_filesFileReceivedFragment(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; var Cancel: Boolean);
    procedure server_filesFileSent(Connection: TsgcWSConnection; const aMessage:
        TsgcWSMessageFile);
    procedure server_filesFileSentAcknowledgment(Connection: TsgcWSConnection;
        const aMessage: TsgcWSMessageFile);
    procedure server_filesFileSentError(Connection: TsgcWSConnection; const
        aMessage: TsgcWSMessageFile; const Error: string);
    procedure server_filesFileSentFragmentRequest(const aMessage:
        TsgcWSMessageFile; var Cancel: Boolean);
  private
    FGuid: string;
    FMessage: TsgcWSMessageFile;
    procedure DoFileSentFragment;
    procedure DoFileReceivedFragment;
    procedure DoSendFile;
    procedure DoBroadcastFile;
    procedure DoStart;
    procedure DoStop;
    procedure DoSyncLog(const aText: String);
  end;

var
  Form6: TForm6;

implementation

{$R *.dfm}

procedure TForm6.btnBroadcastClick(Sender: TObject);
begin
  DoBroadcastFile;
end;

procedure TForm6.FormCreate(Sender: TObject);
begin
  DoStart;
end;

procedure TForm6.btnSaveDirectoryClick(Sender: TObject);
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

procedure TForm6.btnSendClick(Sender: TObject);
begin
  DoSendFile;
end;

procedure TForm6.btnStartClick(Sender: TObject);
begin
  DoStart;
end;

procedure TForm6.btnStopClick(Sender: TObject);
begin
  DoStop;
end;

procedure TForm6.DoBroadcastFile;
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    if oDialog.Execute then
      server_files.BroadcastFile(oDialog.FileName, '', 'test');
  Finally
    FreeAndNil(oDialog);
  End;
end;

procedure TForm6.DoFileReceivedFragment;
begin
  lblFileReceived.Caption := FMessage.FileName + ' ' + IntToStr(FMessage.FilePosition);

  progFileReceived.Position := FMessage.FilePosition;
  progFileReceived.Max := FMessage.FileSize;
end;

procedure TForm6.DoFileSentFragment;
begin
  lblFileSent.Caption := FMessage.FileName + ' ' + IntToStr(FMessage.FilePosition);

  progFileSent.Position := FMessage.FilePosition;
  progFileSent.Max := FMessage.FileSize;
end;

procedure TForm6.DoSendFile;
var
  oDialog: TOpenDialog;
begin
  if FGuid = '' then
    raise Exception.Create('There is no client connected');

  oDialog := TOpenDialog.Create(nil);
  Try
    if oDialog.Execute then
      server_files.SendFile(FGuid, oDialog.FileName);
  Finally
    FreeAndNil(oDialog);
  End;
end;

procedure TForm6.DoStart;
begin
  server_files.Files.BufferSize := TrackSize.Position;
  server_files.Files.QoS.Level := TwsQoS(Ord(cboQoS.ItemIndex));
  server_files.Files.SaveDirectory := txtSaveDirectory.Text;

  server.Port := StrToInt(txtPort.Text);
  server.NotifyEvents := neNoSync;
  server.Active := True;

  DoSyncLog('Server Started');
end;

procedure TForm6.DoStop;
begin
  server.Active := False;

  DoSyncLog('Server Stopped');
end;

procedure TForm6.DoSyncLog(const aText: String);
begin
  TThread.Queue(nil,
    procedure
    begin;
      memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ': ' + aText);
    end);
end;

procedure TForm6.server_filesConnect(Connection: TsgcWSConnection);
begin
  FGuid := Connection.Guid;

  DoSyncLog('Connected: ' + Connection.Guid);
end;

procedure TForm6.server_filesDisconnect(Connection: TsgcWSConnection; Code:
    Integer);
begin
  FGuid := '';

  DoSyncLog('Disconnected: ' + Connection.Guid);
end;

procedure TForm6.server_filesFileReceived(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('File ' + aMessage.FileName + ' has been received successfully.');
end;

procedure TForm6.server_filesFileReceivedError(Connection: TsgcWSConnection;
    const aMessage: TsgcWSMessageFile; const Error: string);
begin
  DoSyncLog('File Received Error ' + aMessage.FileName + ': ' + Error);
end;

procedure TForm6.server_filesFileReceivedFragment(Connection: TsgcWSConnection;
    const aMessage: TsgcWSMessageFile; var Cancel: Boolean);
begin
  FMessage := aMessage;

  NotifyMethod(DoFileReceivedFragment);
end;

procedure TForm6.server_filesFileSent(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('File ' + aMessage.FileName + ' has been sent successfully.');
end;

procedure TForm6.server_filesFileSentAcknowledgment(Connection:
    TsgcWSConnection; const aMessage: TsgcWSMessageFile);
begin
  DoSyncLog('Received Acknowledgment ' + aMessage.Id);
end;

procedure TForm6.server_filesFileSentError(Connection: TsgcWSConnection; const
    aMessage: TsgcWSMessageFile; const Error: string);
begin
  DoSyncLog('File Sent Error ' + aMessage.FileName + ': ' + Error);
end;

procedure TForm6.server_filesFileSentFragmentRequest(const aMessage:
    TsgcWSMessageFile; var Cancel: Boolean);
begin
  FMessage := aMessage;

  NotifyMethod(DoFileSentFragment);
end;

end.
```

