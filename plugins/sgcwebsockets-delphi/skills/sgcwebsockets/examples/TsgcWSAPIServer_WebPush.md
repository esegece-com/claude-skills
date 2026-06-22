# TsgcWSAPIServer_WebPush - Example

Full source of `FWebPush_Server.pas` from the **20.HTTP_Protocol/11.WebPush_Notifications** demo, which uses `TsgcWSAPIServer_WebPush`.

API reference: [TsgcWSAPIServer_WebPush](../reference/api/TsgcWSAPIServer_WebPush.md)
Source demo: `20.HTTP_Protocol/11.WebPush_Notifications` (file `FWebPush_Server.pas`)

```pascal
unit FWebPush_Server;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils,
  // indy
  IdContext,
  // sgc
  sgcBase_Classes, sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_Types,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcIdCustomHTTPServer, sgcSocket_Classes, sgcHTTP_Classes, sgcHTTP,
  sgcWebSocket_Server_API_WebPush, sgcWebSocket_Server_APIs,
  sgcHTTP_API_WebPush;

type
  TWebPushSubscriptions = class(TStringList)
  public
    function AddSubscription(const aSubscription
      : TsgcHTTP_API_WebPush_PushSubscription): Boolean;
    procedure RemoveSubscription(const aSubscription
      : TsgcHTTP_API_WebPush_PushSubscription);
  end;

  TFRMWebPushServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    Label1: TLabel;
    Label2: TLabel;
    txtHost: TEdit;
    Label3: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    pnlLeft: TPanel;
    pnlOptions: TPanel;
    memoLog: TMemo;
    Server: TsgcWebSocketHTTPServer;
    WebPushServer: TsgcWSAPIServer_WebPush;
    Label4: TLabel;
    memoPEMPrivateKey: TMemo;
    Label5: TLabel;
    txtDERPublicKey: TEdit;
    Label6: TLabel;
    txtDERPrivateKey: TEdit;
    pnlBrowsers: TPanel;
    btnChrome: TButton;
    btnEdge: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    pnlBottom: TPanel;
    btnBroadcast: TButton;
    txtBody: TEdit;
    procedure btnBroadcastClick(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnEdgeClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure serverShutdown(Sender: TObject);
    procedure serverStartup(Sender: TObject);
    procedure WebPushServerWebPushSubscription(Sender: TObject;
      aSubscription: TsgcHTTP_API_WebPush_PushSubscription;
      var ResponseCode: Integer);
    procedure WebPushServerWebPushUnsubscription(Sender: TObject;
      aSubscription: TsgcHTTP_API_WebPush_PushSubscription;
      var ResponseCode: Integer);
  private
    FSubscriptions: TWebPushSubscriptions;
    procedure DoLog(const aText: String);
    procedure DoOpenBrowser(const aBrowserName: string);
    function GetSubscriptions: TWebPushSubscriptions;
  public
    destructor Destroy; override;
  public
    property Subscriptions: TWebPushSubscriptions read GetSubscriptions
      write FSubscriptions;
  end;

var
  FRMWebPushServer: TFRMWebPushServer;

implementation

uses
  ShellAPI,
  sgcBase_Helpers;

{$R *.dfm}

destructor TFRMWebPushServer.Destroy;
begin
  FreeAndNil(FSubscriptions);
  inherited;
end;

procedure TFRMWebPushServer.btnBroadcastClick(Sender: TObject);
var
  oMessage: TsgcWebPushMessage;
begin
  oMessage := TsgcWebPushMessage.Create;
  Try
    oMessage.Title := 'eSeGeCe Notification';
    oMessage.Body := txtBody.Text;
    oMessage.Icon := 'https://www.esegece.com/images/esegece_logo_small.png';
    oMessage.Url := 'https://www.esegece.com';

    WebPushServer.BroadcastNotification(oMessage);
  Finally
    sgcFree(oMessage);
  End;
end;

procedure TFRMWebPushServer.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TFRMWebPushServer.btnEdgeClick(Sender: TObject);
begin
  DoOpenBrowser('msedge');
end;

procedure TFRMWebPushServer.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TFRMWebPushServer.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TFRMWebPushServer.FormCreate(Sender: TObject);
var
  i: Integer;
  oList: TStringList;
  oSubscription: TsgcHTTP_API_WebPush_PushSubscription;
begin
  if FileExists('subscriptions.txt') then
  begin
    Subscriptions.LoadFromFile('subscriptions.txt');

    for i := 0 to Subscriptions.Count - 1 do
    begin
      oList := TStringList.Create;
      Try
        oList.Delimiter := Chr(9);
        oList.StrictDelimiter := True;
        oList.DelimitedText := Subscriptions[i];

        if oList.Count = 3 then
        begin
          oSubscription := TsgcHTTP_API_WebPush_PushSubscription.Create;
          Try
            oSubscription.Endpoint := oList[0];
            oSubscription.PublicKey := oList[1];
            oSubscription.AuthSecret := oList[2];

            WebPushServer.Subscriptions.AddSubscription(oSubscription)
          Finally
            sgcFree(oSubscription);
          End;
        end;
      Finally
        sgcFree(oList);
      End;
    end;
  end;

  btnStart.Click;
end;

procedure TFRMWebPushServer.btnStartClick(Sender: TObject);
begin
  // ... webpush config
  WebPushServer.WebPush.VAPID.PEM.PrivateKey.Text :=
    memoPEMPrivateKey.Lines.Text;
  WebPushServer.WebPush.VAPID.DER.PublicKey := txtDERPublicKey.Text;
  WebPushServer.WebPush.VAPID.DER.PrivateKey := txtDERPrivateKey.Text;

  // ... bindings
  Server.Port := StrToInt(txtDefaultPort.Text);
  Server.Bindings.Clear;
  With Server.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... active
  Server.Active := True;
end;

procedure TFRMWebPushServer.btnStopClick(Sender: TObject);
begin
  Server.Active := False;
end;

procedure TFRMWebPushServer.DoLog(const aText: String);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TFRMWebPushServer.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'http';
  vPort := txtDefaultPort.Text;

{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
    PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort +
    WebPushServer.WebPush.Endpoints.Home.Endpoint), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
    PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort +
    WebPushServer.WebPush.Endpoints.Home.Endpoint), '', 0);
{$ENDIF}
end;

function TFRMWebPushServer.GetSubscriptions: TWebPushSubscriptions;
begin
  if not Assigned(FSubscriptions) then
    FSubscriptions := TWebPushSubscriptions.Create;
  Result := FSubscriptions;
end;

procedure TFRMWebPushServer.serverShutdown(Sender: TObject);
begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMWebPushServer.serverStartup(Sender: TObject);
begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMWebPushServer.WebPushServerWebPushSubscription(Sender: TObject;
aSubscription: TsgcHTTP_API_WebPush_PushSubscription;
var ResponseCode: Integer);
var
  oMessage: TsgcWebPushMessage;
begin
  if Subscriptions.AddSubscription(aSubscription) then
  begin
    Subscriptions.SaveToFile('subscriptions.txt');
    oMessage := TsgcWebPushMessage.Create;
    Try
      oMessage.Title := 'eSeGeCe Notification';
      oMessage.Body := 'Subscription Successfully Registered!!!';
      oMessage.Icon := 'https://www.esegece.com/images/esegece_logo_small.png';
      oMessage.Url := 'https://www.esegece.com';

      WebPushServer.SendNotification(aSubscription, oMessage);
    Finally
      sgcFree(oMessage);
    End;
  end;
end;

procedure TFRMWebPushServer.WebPushServerWebPushUnsubscription(Sender: TObject;
aSubscription: TsgcHTTP_API_WebPush_PushSubscription;
var ResponseCode: Integer);
begin
  Subscriptions.RemoveSubscription(aSubscription);
  Subscriptions.SaveToFile('subscriptions.txt');
end;

function TWebPushSubscriptions.AddSubscription(const aSubscription
  : TsgcHTTP_API_WebPush_PushSubscription): Boolean;
var
  i: Integer;
begin
  Result := False;
  // ... check if exists
  for i := Count - 1 downto 0 do
  begin
    if LeftStr(self[i], Length(aSubscription.Endpoint)) = aSubscription.Endpoint
    then
      exit;
  end;
  // ... add the subscription to the list if not exists
  Add(aSubscription.Endpoint + Chr(9) + aSubscription.PublicKey + Chr(9) +
    aSubscription.AuthSecret);
  Result := True;
end;

procedure TWebPushSubscriptions.RemoveSubscription(const aSubscription
  : TsgcHTTP_API_WebPush_PushSubscription);
var
  i: Integer;
begin
  // ... remove the subscription from the list if exists
  for i := Count - 1 downto 0 do
  begin
    if LeftStr(self[i], Length(aSubscription.Endpoint)) = aSubscription.Endpoint
    then
    begin
      Delete(i);
      break;
    end;
  end;
end;

end.
```

