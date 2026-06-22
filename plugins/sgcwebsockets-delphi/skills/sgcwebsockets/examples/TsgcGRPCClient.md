# TsgcGRPCClient - Example

Full source of `FGRPCClient.pas` from the **21.GRPC/01.GRPC_Client** demo, which uses `TsgcGRPCClient`.

API reference: [TsgcGRPCClient](../reference/api/TsgcGRPCClient.md)
Source demo: `21.GRPC/01.GRPC_Client` (file `FGRPCClient.pas`)

```pascal
{ ***************************************************************************
  sgcWebSocket component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit FGRPCClient;

interface

uses
  Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, ComCtrls, Grids,
  // sgc
  sgcHTTP2_Client, sgcHTTP, sgcGRPC_Types, sgcGRPC_Client,
  sgcGRPC_Interceptors, sgcGRPC_Retry, sgcGRPC_LoadBalancing,
  sgcGRPC_HealthCheck, sgcGRPC_Reflection, sgcGRPC_OpenTelemetry, sgcProtoBuf,
  sgcWebSocket_Types;

type
  TFrmGRPCClient = class(TForm)
    pnlTop: TPanel;
    lblHost: TLabel;
    lblPort: TLabel;
    edtHost: TEdit;
    edtPort: TEdit;
    chkTLS: TCheckBox;
    btnConnect: TButton;
    btnDisconnect: TButton;
    pgcMain: TPageControl;
    tabUnary: TTabSheet;
    tabServerStream: TTabSheet;
    tabClientStream: TTabSheet;
    tabBidi: TTabSheet;
    tabSettings: TTabSheet;
    tabMetadata: TTabSheet;
    pnlLog: TPanel;
    lblLog: TLabel;
    memoLog: TMemo;
    splLog: TSplitter;
    { Unary tab }
    lblUnaryService: TLabel;
    edtUnaryService: TEdit;
    lblUnaryMethod: TLabel;
    edtUnaryMethod: TEdit;
    lblUnaryRequest: TLabel;
    memoUnaryRequest: TMemo;
    btnUnarySend: TButton;
    lblUnaryResponse: TLabel;
    memoUnaryResponse: TMemo;
    { Server Streaming tab }
    lblSSService: TLabel;
    edtSSService: TEdit;
    lblSSMethod: TLabel;
    edtSSMethod: TEdit;
    lblSSRequest: TLabel;
    memoSSRequest: TMemo;
    btnSSStart: TButton;
    lblSSMessages: TLabel;
    memoSSMessages: TMemo;
    { Client Streaming tab }
    lblCSService: TLabel;
    edtCSService: TEdit;
    lblCSMethod: TLabel;
    edtCSMethod: TEdit;
    btnCSOpen: TButton;
    lblCSMessage: TLabel;
    edtCSMessage: TEdit;
    btnCSSend: TButton;
    btnCSClose: TButton;
    lblCSResponse: TLabel;
    memoCSResponse: TMemo;
    { Bidi tab }
    lblBidiService: TLabel;
    edtBidiService: TEdit;
    lblBidiMethod: TLabel;
    edtBidiMethod: TEdit;
    btnBidiOpen: TButton;
    lblBidiMessage: TLabel;
    edtBidiMessage: TEdit;
    btnBidiSend: TButton;
    btnBidiClose: TButton;
    lblBidiMessages: TLabel;
    memoBidiMessages: TMemo;
    { Settings tab }
    lblCompression: TLabel;
    cboCompression: TComboBox;
    lblContentType: TLabel;
    cboContentType: TComboBox;
    lblMaxMsgSize: TLabel;
    edtMaxMsgSize: TEdit;
    lblTimeout: TLabel;
    edtTimeout: TEdit;
    btnApplySettings: TButton;
    { Metadata tab }
    lblMetaKey: TLabel;
    edtMetaKey: TEdit;
    lblMetaValue: TLabel;
    edtMetaValue: TEdit;
    btnMetaAdd: TButton;
    btnMetaRemove: TButton;
    lstMetadata: TListBox;
    { Interceptors tab }
    tabInterceptors: TTabSheet;
    lblInterceptors: TLabel;
    chkLogInterceptor: TCheckBox;
    chkTimeoutInterceptor: TCheckBox;
    lblDefaultTimeout: TLabel;
    edtDefaultTimeout: TEdit;
    chkMetaInterceptor: TCheckBox;
    lblIntMetaKey: TLabel;
    edtIntMetaKey: TEdit;
    lblIntMetaValue: TLabel;
    edtIntMetaValue: TEdit;
    btnIntMetaAdd: TButton;
    lstIntHeaders: TListBox;
    btnIntApply: TButton;
    { Retry tab }
    tabRetry: TTabSheet;
    chkRetryEnabled: TCheckBox;
    lblRetryMaxAttempts: TLabel;
    edtRetryMaxAttempts: TEdit;
    lblRetryInitBackoff: TLabel;
    edtRetryInitBackoff: TEdit;
    lblRetryMaxBackoff: TLabel;
    edtRetryMaxBackoff: TEdit;
    lblRetryMultiplier: TLabel;
    edtRetryMultiplier: TEdit;
    lblRetryStatuses: TLabel;
    chkRetryUnavailable: TCheckBox;
    chkRetryResourceExhausted: TCheckBox;
    chkRetryAborted: TCheckBox;
    chkRetryInternal: TCheckBox;
    btnRetryApply: TButton;
    lblRetryStatus: TLabel;
    { Load Balancing tab }
    tabLoadBalancing: TTabSheet;
    lblLBStrategy: TLabel;
    cboLBStrategy: TComboBox;
    lblLBHost: TLabel;
    edtLBHost: TEdit;
    lblLBPort: TLabel;
    edtLBPort: TEdit;
    btnLBAdd: TButton;
    btnLBRemove: TButton;
    lstLBEndpoints: TListBox;
    lblLBResolve: TLabel;
    edtLBTarget: TEdit;
    btnLBResolve: TButton;
    memoLBResolveResult: TMemo;
    { Health Check tab }
    tabHealthCheck: TTabSheet;
    lblHealthService: TLabel;
    edtHealthService: TEdit;
    btnHealthCheck: TButton;
    btnHealthWatch: TButton;
    lblHealthResult: TLabel;
    lblHealthStatus: TLabel;
    memoHealthLog: TMemo;
    { Reflection tab }
    tabReflection: TTabSheet;
    btnReflectList: TButton;
    lstReflectServices: TListBox;
    lblReflectSymbol: TLabel;
    edtReflectSymbol: TEdit;
    btnReflectFile: TButton;
    memoReflectResult: TMemo;
    { Telemetry tab }
    tabTelemetry: TTabSheet;
    chkTelemetryEnabled: TCheckBox;
    chkTracingEnabled: TCheckBox;
    btnTelemetryRefresh: TButton;
    btnTelemetryClear: TButton;
    memoTelemetryStats: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnUnarySendClick(Sender: TObject);
    procedure btnSSStartClick(Sender: TObject);
    procedure btnCSOpenClick(Sender: TObject);
    procedure btnCSSendClick(Sender: TObject);
    procedure btnCSCloseClick(Sender: TObject);
    procedure btnBidiOpenClick(Sender: TObject);
    procedure btnBidiSendClick(Sender: TObject);
    procedure btnBidiCloseClick(Sender: TObject);
    procedure btnApplySettingsClick(Sender: TObject);
    procedure btnMetaAddClick(Sender: TObject);
    procedure btnMetaRemoveClick(Sender: TObject);
    procedure btnIntMetaAddClick(Sender: TObject);
    procedure btnIntApplyClick(Sender: TObject);
    procedure btnRetryApplyClick(Sender: TObject);
    procedure btnLBAddClick(Sender: TObject);
    procedure btnLBRemoveClick(Sender: TObject);
    procedure btnLBResolveClick(Sender: TObject);
    procedure btnHealthCheckClick(Sender: TObject);
    procedure btnHealthWatchClick(Sender: TObject);
    procedure btnReflectListClick(Sender: TObject);
    procedure btnReflectFileClick(Sender: TObject);
    procedure btnTelemetryRefreshClick(Sender: TObject);
    procedure btnTelemetryClearClick(Sender: TObject);
  private
    FHTTP2Client: TsgcHTTP2Client;
    FGRPCClient: TsgcGRPCClient;
    FClientStreamId: Integer;
    FBidiStreamId: Integer;
    FLogInterceptor: TsgcGRPCLoggingInterceptor;
    FTimeoutInterceptor: TsgcGRPCTimeoutInterceptor;
    FMetaInterceptor: TsgcGRPCMetadataInterceptor;
    FLoadBalancer: TsgcGRPCLoadBalancer;
    FHealthClient: TsgcGRPCHealthClient;
    FReflectionClient: TsgcGRPCReflectionClient;
    function GetHTTP2Client: TsgcHTTP2Client;
    function GetGRPCClient: TsgcGRPCClient;
    procedure OnGRPCConnectEvent(Sender: TObject);
    procedure OnGRPCDisconnectEvent(Sender: TObject);
    procedure OnGRPCResponseEvent(Sender: TObject;
      const aResponse: TsgcGRPCResponse);
    procedure OnGRPCStreamMessageEvent(Sender: TObject;
      const aMessage: TsgcGRPCStreamMessage; var aCancel: Boolean);
    procedure OnGRPCStreamEndEvent(Sender: TObject;
      const aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string;
      const aTrailers: TsgcGRPCMetadata);
    procedure OnGRPCErrorEvent(Sender: TObject;
      const aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string);
    procedure OnGRPCExceptionEvent(Sender: TObject; const E: Exception);
    procedure OnGRPCBeforeRequestEvent(Sender: TObject;
      const aService, aMethod: string; var aMetadata: TsgcGRPCMetadata);
    procedure Log(const aText: string);
    procedure AddLineSafe(aMemo: TMemo; const aText: string);
    function StringToBytes(const aText: string): TBytes;
    function BytesToString(const aData: TBytes): string;
    function EncodeProtoString(const aText: string): TBytes;
    function DecodeProtoString(const aData: TBytes): string;
    procedure OnInterceptorLog(Sender: TObject; const aMessage: string);
  end;

var
  FrmGRPCClient: TFrmGRPCClient;

implementation

{$R *.dfm}
{ TFrmGRPCClient }

procedure TFrmGRPCClient.FormCreate(Sender: TObject);
begin
  FHTTP2Client := nil;
  FGRPCClient := nil;
  FClientStreamId := 0;
  FBidiStreamId := 0;
  FLogInterceptor := nil;
  FTimeoutInterceptor := nil;
  FMetaInterceptor := nil;
  FLoadBalancer := nil;
  FHealthClient := nil;
  FReflectionClient := nil;
end;

procedure TFrmGRPCClient.FormDestroy(Sender: TObject);
begin
  if Assigned(FHTTP2Client) then
  begin
    FHTTP2Client.Active := False;
  end;
  FreeAndNil(FLoadBalancer);
  FreeAndNil(FHealthClient);
  FreeAndNil(FReflectionClient);
  FreeAndNil(FGRPCClient);
  FreeAndNil(FHTTP2Client);
end;

function TFrmGRPCClient.GetHTTP2Client: TsgcHTTP2Client;
begin
  if not Assigned(FHTTP2Client) then
  begin
    FHTTP2Client := TsgcHTTP2Client.Create(nil);
    { Deliver gRPC events from the reader thread so the synchronous Call
      (Health Check / Reflection) does not deadlock the UI thread. UI
      updates in the async event handlers are marshaled to the main thread. }
    FHTTP2Client.NotifyEvents := neNoSync;
  end;
  Result := FHTTP2Client;
end;

function TFrmGRPCClient.GetGRPCClient: TsgcGRPCClient;
begin
  if not Assigned(FGRPCClient) then
  begin
    FGRPCClient := TsgcGRPCClient.Create(nil);
    FGRPCClient.Client := GetHTTP2Client;
    FGRPCClient.OnGRPCConnect := OnGRPCConnectEvent;
    FGRPCClient.OnGRPCDisconnect := OnGRPCDisconnectEvent;
    FGRPCClient.OnGRPCResponse := OnGRPCResponseEvent;
    FGRPCClient.OnGRPCStreamMessage := OnGRPCStreamMessageEvent;
    FGRPCClient.OnGRPCStreamEnd := OnGRPCStreamEndEvent;
    FGRPCClient.OnGRPCError := OnGRPCErrorEvent;
    FGRPCClient.OnGRPCException := OnGRPCExceptionEvent;
    FGRPCClient.OnGRPCBeforeRequest := OnGRPCBeforeRequestEvent;
  end;
  Result := FGRPCClient;
end;

procedure TFrmGRPCClient.OnGRPCConnectEvent(Sender: TObject);
begin
  Log('Connected to gRPC server');
end;

procedure TFrmGRPCClient.OnGRPCDisconnectEvent(Sender: TObject);
begin
  Log('Disconnected from gRPC server');
end;

procedure TFrmGRPCClient.OnGRPCResponseEvent(Sender: TObject;
  const aResponse: TsgcGRPCResponse);
var
  vData: string;
begin
  vData := DecodeProtoString(aResponse.Data);
  Log('Response [status=' + IntToStr(Ord(aResponse.StatusCode)) + ']: '
    + vData);
  AddLineSafe(memoUnaryResponse, vData);
end;

procedure TFrmGRPCClient.OnGRPCStreamMessageEvent(Sender: TObject;
  const aMessage: TsgcGRPCStreamMessage; var aCancel: Boolean);
var
  vData: string;
begin
  vData := DecodeProtoString(aMessage.Data);
  Log('Stream message [stream=' + IntToStr(aMessage.StreamId) + ']: ' + vData);
  AddLineSafe(memoSSMessages, vData);
  AddLineSafe(memoBidiMessages, vData);
end;

procedure TFrmGRPCClient.OnGRPCStreamEndEvent(Sender: TObject;
  const aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string;
  const aTrailers: TsgcGRPCMetadata);
begin
  Log('Stream ended [status=' + IntToStr(Ord(aStatusCode)) + ']: ' +
    aStatusMessage);
end;

procedure TFrmGRPCClient.OnGRPCErrorEvent(Sender: TObject;
  const aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string);
begin
  Log('Error [status=' + IntToStr(Ord(aStatusCode)) + ']: ' + aStatusMessage);
end;

procedure TFrmGRPCClient.OnGRPCExceptionEvent(Sender: TObject;
  const E: Exception);
begin
  Log('Exception: ' + E.Message);
end;

procedure TFrmGRPCClient.OnGRPCBeforeRequestEvent(Sender: TObject;
  const aService, aMethod: string; var aMetadata: TsgcGRPCMetadata);
begin
  Log('Before request: /' + aService + '/' + aMethod);
end;

procedure TFrmGRPCClient.AddLineSafe(aMemo: TMemo; const aText: string);
var
  oMemo: TMemo;
  vText: string;
begin
  oMemo := aMemo;
  vText := aText;
  if GetCurrentThreadId = MainThreadID then
    oMemo.Lines.Add(vText)
  else
    TThread.Queue(nil, procedure
      begin
        oMemo.Lines.Add(vText);
      end);
end;

procedure TFrmGRPCClient.Log(const aText: string);
begin
  AddLineSafe(memoLog, FormatDateTime('hh:nn:ss.zzz', Now) + ' ' + aText);
end;

function TFrmGRPCClient.StringToBytes(const aText: string): TBytes;
var
  vLen: Integer;
begin
  vLen := Length(aText);
  SetLength(Result, vLen);
  if vLen > 0 then
    Move(aText[1], Result[0], vLen);
end;

function TFrmGRPCClient.BytesToString(const aData: TBytes): string;
var
  vLen: Integer;
begin
  Result := '';
  vLen := Length(aData);
  if vLen > 0 then
  begin
    SetLength(Result, vLen);
    Move(aData[0], Result[1], vLen);
  end;
end;

function TFrmGRPCClient.EncodeProtoString(const aText: string): TBytes;
var
  oWriter: TsgcProtobufWriter;
begin
  if aText = '' then
  begin
    SetLength(Result, 0);
    Exit;
  end;
  oWriter := TsgcProtobufWriter.Create;
  try
    oWriter.WriteString(1, aText);
    Result := oWriter.ToBytes;
  finally
    oWriter.Free;
  end;
end;

function TFrmGRPCClient.DecodeProtoString(const aData: TBytes): string;
var
  oMsg: TsgcProtobufMessage;
  oField: TsgcProtobufField;
begin
  Result := '';
  if Length(aData) = 0 then
    Exit;
  oMsg := TsgcProtobufMessage.Create;
  try
    oMsg.LoadFromBytes(aData);
    oField := oMsg.FindField(1);
    if Assigned(oField) then
      Result := oField.AsString;
  finally
    oMsg.Free;
  end;
  if Result = '' then
    Result := BytesToString(aData);
end;

procedure TFrmGRPCClient.btnConnectClick(Sender: TObject);
begin
  GetHTTP2Client.Host := edtHost.Text;
  GetHTTP2Client.Port := StrToInt(edtPort.Text);
  GetHTTP2Client.TLS := chkTLS.Checked;
  GetGRPCClient;
  Log('Connecting to ' + edtHost.Text + ':' + edtPort.Text + '...');
  GetHTTP2Client.Active := True;
end;

procedure TFrmGRPCClient.btnDisconnectClick(Sender: TObject);
begin
  if Assigned(FHTTP2Client) then
  begin
    FHTTP2Client.Active := False;
    Log('Disconnecting...');
  end;
end;

procedure TFrmGRPCClient.btnUnarySendClick(Sender: TObject);
var
  vData: TBytes;
begin
  memoUnaryResponse.Lines.Clear;
  vData := EncodeProtoString(Trim(memoUnaryRequest.Lines.Text));
  GetGRPCClient.CallAsync(edtUnaryService.Text, edtUnaryMethod.Text, vData);
  Log('Unary call: /' + edtUnaryService.Text + '/' + edtUnaryMethod.Text);
end;

procedure TFrmGRPCClient.btnSSStartClick(Sender: TObject);
var
  vData: TBytes;
begin
  memoSSMessages.Lines.Clear;
  vData := EncodeProtoString(Trim(memoSSRequest.Lines.Text));
  GetGRPCClient.ServerStreamingCall(edtSSService.Text, edtSSMethod.Text, vData);
  Log('Server streaming: /' + edtSSService.Text + '/' + edtSSMethod.Text);
end;

procedure TFrmGRPCClient.btnCSOpenClick(Sender: TObject);
begin
  FClientStreamId := GetGRPCClient.OpenClientStream(edtCSService.Text,
    edtCSMethod.Text);
  Log('Client stream opened [id=' + IntToStr(FClientStreamId) + ']: /' +
    edtCSService.Text + '/' + edtCSMethod.Text);
end;

procedure TFrmGRPCClient.btnCSSendClick(Sender: TObject);
var
  vData: TBytes;
begin
  if FClientStreamId > 0 then
  begin
    vData := EncodeProtoString(edtCSMessage.Text);
    GetGRPCClient.SendStreamMessage(FClientStreamId, vData);
    Log('Client stream message sent [id=' + IntToStr(FClientStreamId) + ']');
  end
  else
    Log('No client stream open');
end;

procedure TFrmGRPCClient.btnCSCloseClick(Sender: TObject);
begin
  if FClientStreamId > 0 then
  begin
    GetGRPCClient.CloseClientStreamAsync(FClientStreamId);
    Log('Client stream closed [id=' + IntToStr(FClientStreamId) + ']');
    FClientStreamId := 0;
  end;
end;

procedure TFrmGRPCClient.btnBidiOpenClick(Sender: TObject);
begin
  FBidiStreamId := GetGRPCClient.OpenBidiStream(edtBidiService.Text,
    edtBidiMethod.Text);
  Log('Bidi stream opened [id=' + IntToStr(FBidiStreamId) + ']: /' +
    edtBidiService.Text + '/' + edtBidiMethod.Text);
end;

procedure TFrmGRPCClient.btnBidiSendClick(Sender: TObject);
var
  vData: TBytes;
begin
  if FBidiStreamId > 0 then
  begin
    vData := EncodeProtoString(edtBidiMessage.Text);
    GetGRPCClient.SendBidiMessage(FBidiStreamId, vData);
    Log('Bidi message sent [id=' + IntToStr(FBidiStreamId) + ']');
  end
  else
    Log('No bidi stream open');
end;

procedure TFrmGRPCClient.btnBidiCloseClick(Sender: TObject);
begin
  if FBidiStreamId > 0 then
  begin
    GetGRPCClient.CloseBidiStream(FBidiStreamId);
    Log('Bidi stream closed [id=' + IntToStr(FBidiStreamId) + ']');
    FBidiStreamId := 0;
  end;
end;

procedure TFrmGRPCClient.btnApplySettingsClick(Sender: TObject);
begin
  GetGRPCClient.ChannelOptions.Compression :=
    TsgcGRPCCompression(cboCompression.ItemIndex);
  GetGRPCClient.ChannelOptions.ContentType :=
    TsgcGRPCContentType(cboContentType.ItemIndex);
  GetGRPCClient.ChannelOptions.MaxMessageSize :=
    StrToIntDef(edtMaxMsgSize.Text, 4194304);
  Log('Channel options applied');
end;

procedure TFrmGRPCClient.btnMetaAddClick(Sender: TObject);
begin
  if (edtMetaKey.Text <> '') then
  begin
    GetGRPCClient.DefaultMetadata.Add(edtMetaKey.Text, edtMetaValue.Text);
    lstMetadata.Items.Add(edtMetaKey.Text + ': ' + edtMetaValue.Text);
    Log('Metadata added: ' + edtMetaKey.Text + '=' + edtMetaValue.Text);
    edtMetaKey.Text := '';
    edtMetaValue.Text := '';
  end;
end;

procedure TFrmGRPCClient.btnMetaRemoveClick(Sender: TObject);
begin
  if lstMetadata.ItemIndex >= 0 then
  begin
    Log('Metadata removed: ' + lstMetadata.Items[lstMetadata.ItemIndex]);
    GetGRPCClient.DefaultMetadata.Items.Delete(lstMetadata.ItemIndex);
    lstMetadata.Items.Delete(lstMetadata.ItemIndex);
  end;
end;

procedure TFrmGRPCClient.OnInterceptorLog(Sender: TObject;
const aMessage: string);
begin
  Log('[Interceptor] ' + aMessage);
end;

procedure TFrmGRPCClient.btnIntMetaAddClick(Sender: TObject);
begin
  if edtIntMetaKey.Text <> '' then
  begin
    lstIntHeaders.Items.Add(edtIntMetaKey.Text + ': ' + edtIntMetaValue.Text);
    edtIntMetaKey.Text := '';
    edtIntMetaValue.Text := '';
  end;
end;

procedure TFrmGRPCClient.btnIntApplyClick(Sender: TObject);
var
  i: Integer;
  vPos: Integer;
  vLine: string;
begin
  { Clear existing interceptors }
  GetGRPCClient.Interceptors.Clear;
  FreeAndNil(FLogInterceptor);
  FreeAndNil(FTimeoutInterceptor);
  FreeAndNil(FMetaInterceptor);

  { Logging interceptor }
  if chkLogInterceptor.Checked then
  begin
    FLogInterceptor := TsgcGRPCLoggingInterceptor.Create;
    FLogInterceptor.OnLog := OnInterceptorLog;
    GetGRPCClient.Interceptors.Add(FLogInterceptor);
    Log('Logging interceptor enabled');
  end;

  { Timeout interceptor }
  if chkTimeoutInterceptor.Checked then
  begin
    FTimeoutInterceptor := TsgcGRPCTimeoutInterceptor.Create;
    FTimeoutInterceptor.DefaultTimeout :=
      StrToIntDef(edtDefaultTimeout.Text, 30000);
    GetGRPCClient.Interceptors.Add(FTimeoutInterceptor);
    Log('Timeout interceptor enabled (' + edtDefaultTimeout.Text + 'ms)');
  end;

  { Metadata interceptor }
  if chkMetaInterceptor.Checked then
  begin
    FMetaInterceptor := TsgcGRPCMetadataInterceptor.Create;
    for i := 0 to lstIntHeaders.Items.Count - 1 do
    begin
      vLine := lstIntHeaders.Items[i];
      vPos := Pos(':', vLine);
      if vPos > 0 then
        FMetaInterceptor.Headers.Add(Trim(Copy(vLine, 1, vPos - 1)),
          Trim(Copy(vLine, vPos + 1, Length(vLine) - vPos)));
    end;
    GetGRPCClient.Interceptors.Add(FMetaInterceptor);
    Log('Metadata interceptor enabled (' + IntToStr(lstIntHeaders.Items.Count) +
      ' headers)');
  end;

  Log('Interceptors applied: ' + IntToStr(GetGRPCClient.Interceptors.Count) +
    ' active');
end;

procedure TFrmGRPCClient.btnRetryApplyClick(Sender: TObject);
begin
  GetGRPCClient.RetryPolicy.Enabled := chkRetryEnabled.Checked;
  GetGRPCClient.RetryPolicy.MaxAttempts :=
    StrToIntDef(edtRetryMaxAttempts.Text, 3);
  GetGRPCClient.RetryPolicy.InitialBackoff :=
    StrToIntDef(edtRetryInitBackoff.Text, 100);
  GetGRPCClient.RetryPolicy.MaxBackoff :=
    StrToIntDef(edtRetryMaxBackoff.Text, 30000);
  GetGRPCClient.RetryPolicy.BackoffMultiplier :=
    StrToFloatDef(edtRetryMultiplier.Text, 2.0);

  GetGRPCClient.RetryPolicy.RetryableStatusCodes := [];
  if chkRetryUnavailable.Checked then
    GetGRPCClient.RetryPolicy.RetryableStatusCodes :=
      GetGRPCClient.RetryPolicy.RetryableStatusCodes + [grpcUNAVAILABLE];
  if chkRetryResourceExhausted.Checked then
    GetGRPCClient.RetryPolicy.RetryableStatusCodes :=
      GetGRPCClient.RetryPolicy.RetryableStatusCodes + [grpcRESOURCE_EXHAUSTED];
  if chkRetryAborted.Checked then
    GetGRPCClient.RetryPolicy.RetryableStatusCodes :=
      GetGRPCClient.RetryPolicy.RetryableStatusCodes + [grpcABORTED];
  if chkRetryInternal.Checked then
    GetGRPCClient.RetryPolicy.RetryableStatusCodes :=
      GetGRPCClient.RetryPolicy.RetryableStatusCodes + [grpcINTERNAL];

  if chkRetryEnabled.Checked then
    lblRetryStatus.Caption := 'Retry ENABLED (max ' + edtRetryMaxAttempts.Text +
      ' attempts)'
  else
    lblRetryStatus.Caption := 'Retry DISABLED';
  Log('Retry policy applied: enabled=' +
    BoolToStr(chkRetryEnabled.Checked, True));
end;

procedure TFrmGRPCClient.btnLBAddClick(Sender: TObject);
begin
  if not Assigned(FLoadBalancer) then
    FLoadBalancer := TsgcGRPCLoadBalancer.Create
      (TsgcGRPCLoadBalancerType(cboLBStrategy.ItemIndex));
  FLoadBalancer.Endpoints.Add(edtLBHost.Text,
    StrToIntDef(edtLBPort.Text, 50051));
  lstLBEndpoints.Items.Add(edtLBHost.Text + ':' + edtLBPort.Text);
  Log('Endpoint added: ' + edtLBHost.Text + ':' + edtLBPort.Text);
end;

procedure TFrmGRPCClient.btnLBRemoveClick(Sender: TObject);
begin
  if (lstLBEndpoints.ItemIndex >= 0) and Assigned(FLoadBalancer) then
  begin
    Log('Endpoint removed: ' + lstLBEndpoints.Items[lstLBEndpoints.ItemIndex]);
    FLoadBalancer.Endpoints.Remove(lstLBEndpoints.ItemIndex);
    lstLBEndpoints.Items.Delete(lstLBEndpoints.ItemIndex);
  end;
end;

procedure TFrmGRPCClient.btnLBResolveClick(Sender: TObject);
var
  oResolver: TsgcGRPCNameResolver;
  oEndpoints: TsgcGRPCEndpointList;
  i: Integer;
  oEP: TsgcGRPCEndpoint;
begin
  memoLBResolveResult.Lines.Clear;
  oResolver := TsgcGRPCNameResolver.Create;
  try
    oEndpoints := oResolver.Resolve(edtLBTarget.Text);
    try
      memoLBResolveResult.Lines.Add('Resolved ' + IntToStr(oEndpoints.Count) +
        ' endpoint(s) for: ' + edtLBTarget.Text);
      for i := 0 to oEndpoints.Count - 1 do
      begin
        oEP := oEndpoints.GetEndpoint(i);
        memoLBResolveResult.Lines.Add('  ' + oEP.Host + ':' +
          IntToStr(oEP.Port));
      end;
      Log('DNS resolved: ' + edtLBTarget.Text + ' -> ' +
        IntToStr(oEndpoints.Count) + ' endpoints');
    finally
      oEndpoints.Free;
    end;
  finally
    oResolver.Free;
  end;
end;

procedure TFrmGRPCClient.btnHealthCheckClick(Sender: TObject);
var
  oHealth: TsgcGRPCHealthClient;
  vReqBytes: TBytes;
  oResponse: TsgcGRPCResponse;
  vStatus: TsgcGRPCServingStatus;
begin
  oHealth := TsgcGRPCHealthClient.Create;
  try
    vReqBytes := oHealth.BuildCheckRequest(edtHealthService.Text);
    oResponse := GetGRPCClient.Call(TsgcGRPCHealthClient.ServiceName,
      TsgcGRPCHealthClient.CheckMethodName, vReqBytes);
    try
      if Assigned(oResponse) and (oResponse.StatusCode = grpcOK) then
      begin
        vStatus := oHealth.ParseCheckResponse(oResponse.Data);
        lblHealthStatus.Caption := sgcGRPCServingStatusToStr(vStatus);
        memoHealthLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) +
          ' Health check: ' + edtHealthService.Text + ' -> ' +
          sgcGRPCServingStatusToStr(vStatus));
        Log('Health check: ' + sgcGRPCServingStatusToStr(vStatus));
      end
      else
      begin
        lblHealthStatus.Caption := 'ERROR';
        if Assigned(oResponse) then
          memoHealthLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) +
            ' Health check failed: ' + oResponse.StatusMessage)
        else
          memoHealthLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) +
            ' Health check failed: no response');
      end;
    finally
      oResponse.Free;
    end;
  finally
    oHealth.Free;
  end;
end;

procedure TFrmGRPCClient.btnHealthWatchClick(Sender: TObject);
var
  oHealth: TsgcGRPCHealthClient;
  vReqBytes: TBytes;
begin
  oHealth := TsgcGRPCHealthClient.Create;
  try
    vReqBytes := oHealth.BuildWatchRequest(edtHealthService.Text);
    GetGRPCClient.ServerStreamingCall(TsgcGRPCHealthClient.ServiceName,
      TsgcGRPCHealthClient.WatchMethodName, vReqBytes);
    memoHealthLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) +
      ' Watch started for: ' + edtHealthService.Text);
    Log('Health watch started: ' + edtHealthService.Text);
  finally
    oHealth.Free;
  end;
end;

procedure TFrmGRPCClient.btnReflectListClick(Sender: TObject);
var
  oReflect: TsgcGRPCReflectionClient;
  vReqBytes: TBytes;
  oResponse: TsgcGRPCResponse;
  oReflectResp: TsgcGRPCReflectionResponse;
  i: Integer;
begin
  lstReflectServices.Items.Clear;
  oReflect := TsgcGRPCReflectionClient.Create;
  try
    vReqBytes := oReflect.BuildListServicesRequest;
    oResponse := GetGRPCClient.Call(TsgcGRPCReflectionClient.ServiceName,
      TsgcGRPCReflectionClient.MethodName, vReqBytes);
    try
      if Assigned(oResponse) and (oResponse.StatusCode = grpcOK) then
      begin
        oReflectResp := oReflect.ParseResponse(oResponse.Data);
        try
          for i := 0 to oReflectResp.ServiceNames.Count - 1 do
            lstReflectServices.Items.Add(oReflectResp.ServiceNames[i]);
          Log('Reflection: found ' + IntToStr(oReflectResp.ServiceNames.Count) +
            ' services');
        finally
          oReflectResp.Free;
        end;
      end
      else
      begin
        if Assigned(oResponse) then
          memoReflectResult.Lines.Add('Error: ' + oResponse.StatusMessage)
        else
          memoReflectResult.Lines.Add('Error: no response');
      end;
    finally
      oResponse.Free;
    end;
  finally
    oReflect.Free;
  end;
end;

procedure TFrmGRPCClient.btnReflectFileClick(Sender: TObject);
var
  oReflect: TsgcGRPCReflectionClient;
  vReqBytes: TBytes;
  oResponse: TsgcGRPCResponse;
  oReflectResp: TsgcGRPCReflectionResponse;
  i: Integer;
begin
  memoReflectResult.Lines.Clear;
  if edtReflectSymbol.Text = '' then
  begin
    memoReflectResult.Lines.Add('Enter a symbol name');
    Exit;
  end;
  oReflect := TsgcGRPCReflectionClient.Create;
  try
    vReqBytes := oReflect.BuildFileBySymbolRequest(edtReflectSymbol.Text);
    oResponse := GetGRPCClient.Call(TsgcGRPCReflectionClient.ServiceName,
      TsgcGRPCReflectionClient.MethodName, vReqBytes);
    try
      if Assigned(oResponse) and (oResponse.StatusCode = grpcOK) then
      begin
        oReflectResp := oReflect.ParseResponse(oResponse.Data);
        try
          memoReflectResult.Lines.Add('File descriptors for: ' +
            edtReflectSymbol.Text);
          memoReflectResult.Lines.Add
            ('Count: ' + IntToStr(oReflectResp.FileDescriptorCount));
          for i := 0 to oReflectResp.FileDescriptorCount - 1 do
            memoReflectResult.Lines.Add('  Descriptor ' + IntToStr(i) + ': ' +
              IntToStr(Length(oReflectResp.GetFileDescriptorBytes(i))) +
              ' bytes');
          Log('Reflection: got ' + IntToStr(oReflectResp.FileDescriptorCount) +
            ' file descriptors for ' + edtReflectSymbol.Text);
        finally
          oReflectResp.Free;
        end;
      end
      else
      begin
        if Assigned(oResponse) then
          memoReflectResult.Lines.Add('Error: ' + oResponse.StatusMessage)
        else
          memoReflectResult.Lines.Add('Error: no response');
      end;
    finally
      oResponse.Free;
    end;
  finally
    oReflect.Free;
  end;
end;

procedure TFrmGRPCClient.btnTelemetryRefreshClick(Sender: TObject);
var
  oCollector: TsgcGRPCMetricsCollector;
  oStats: TsgcGRPCMethodStats;
  i: Integer;
begin
  memoTelemetryStats.Lines.Clear;
  oCollector := GetGRPCClient.MetricsCollector;
  oCollector.Enabled := chkTelemetryEnabled.Checked;

  memoTelemetryStats.Lines.Add('=== gRPC Call Metrics ===');
  memoTelemetryStats.Lines.Add('');
  memoTelemetryStats.Lines.Add('Total Calls:      ' +
    IntToStr(oCollector.TotalCalls));
  memoTelemetryStats.Lines.Add('Failed Calls:     ' +
    IntToStr(oCollector.TotalFailedCalls));
  if oCollector.TotalCalls > 0 then
  begin
    memoTelemetryStats.Lines.Add('Success Rate:     ' + FormatFloat('0.0',
      oCollector.GetOverallSuccessRate * 100) + '%');
    memoTelemetryStats.Lines.Add('Avg Latency:      ' + FormatFloat('0.0',
      oCollector.GetTotalAverageDurationMs) + ' ms');
  end;
  memoTelemetryStats.Lines.Add('');
  memoTelemetryStats.Lines.Add('--- Per-Method Stats ---');

  for i := 0 to oCollector.MethodStatsCount - 1 do
  begin
    oStats := oCollector.GetMethodStatsByIndex(i);
    memoTelemetryStats.Lines.Add('');
    memoTelemetryStats.Lines.Add('/' + oStats.Service + '/' + oStats.Method);
    memoTelemetryStats.Lines.Add('  Calls:     ' + IntToStr(oStats.TotalCalls) +
      ' (ok=' + IntToStr(oStats.SuccessCalls) + ' fail=' +
      IntToStr(oStats.FailedCalls) + ')');
    if oStats.TotalCalls > 0 then
    begin
      memoTelemetryStats.Lines.Add('  Avg:       ' + FormatFloat('0.0',
        oStats.GetAverageDurationMs) + ' ms');
      memoTelemetryStats.Lines.Add('  Min/Max:   ' +
        IntToStr(oStats.MinDurationMs) + ' / ' +
        IntToStr(oStats.MaxDurationMs) + ' ms');
      memoTelemetryStats.Lines.Add('  Req bytes: ' +
        IntToStr(oStats.TotalRequestBytes));
      memoTelemetryStats.Lines.Add('  Res bytes: ' +
        IntToStr(oStats.TotalResponseBytes));
    end;
  end;
  Log('Telemetry stats refreshed');
end;

procedure TFrmGRPCClient.btnTelemetryClearClick(Sender: TObject);
begin
  GetGRPCClient.MetricsCollector.Clear;
  memoTelemetryStats.Lines.Clear;
  memoTelemetryStats.Lines.Add('Metrics cleared.');
  Log('Telemetry stats cleared');
end;

end.
```

