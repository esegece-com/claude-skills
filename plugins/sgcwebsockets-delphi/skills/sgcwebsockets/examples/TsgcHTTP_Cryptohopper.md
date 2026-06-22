# TsgcHTTP_Cryptohopper - Example

Full source of `FCryptohopper.pas` from the **50.Other/03.Cryptohopper** demo, which uses `TsgcHTTP_Cryptohopper`.

API reference: [TsgcHTTP_Cryptohopper](../reference/api/TsgcHTTP_Cryptohopper.md)
Source demo: `50.Other/03.Cryptohopper` (file `FCryptohopper.pas`)

```pascal
unit FCryptohopper;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, StdCtrls, ComCtrls, sgcBase_Classes, sgcHTTP_Classes,
  sgcHTTP_API, sgcHTTP_API_Cryptohopper, sgcLibs;

type
  TFRMCryptohopper = class(TForm)
    memoLog: TMemo;
    pnlTop: TPanel;
    pnlBody: TPanel;
    cryptohopper: TsgcHTTP_Cryptohopper;
    txtClientId: TEdit;
    txtClientSecret: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    txtLocalIP: TEdit;
    txtLocalPort: TEdit;
    Label3: TLabel;
    Label4: TLabel;
    pnlMethods: TPanel;
    PageControl1: TPageControl;
    tabHopper: TTabSheet;
    btnGetHoppers: TButton;
    btnGetHopper: TButton;
    btnCreateHopper: TButton;
    btnDeleteHopper: TButton;
    tabOrders: TTabSheet;
    tabPosition: TTabSheet;
    btnGetPosition: TButton;
    btnGetOpenOrders: TButton;
    btnDeleteOrder: TButton;
    btnDeleteAllOrders: TButton;
    btnGetOpenOrder: TButton;
    btnCancelOrder: TButton;
    tabTrades: TTabSheet;
    btnGetTradeHistory: TButton;
    tabExchange: TTabSheet;
    btnGetExchange: TButton;
    btnGetAllTickers: TButton;
    btnGetMarketTicker: TButton;
    btnGetOrderBook: TButton;
    Label76: TLabel;
    Label77: TLabel;
    cboMarketSide: TComboBox;
    txtMarketOrderSize: TEdit;
    cboPlaceMarketOrder: TButton;
    Label79: TLabel;
    Label78: TLabel;
    cboLimitSide: TComboBox;
    Label80: TLabel;
    txtLimitOrderPrice: TEdit;
    txtLimitOrderSize: TEdit;
    cboPlaceLimitOrder: TButton;
    txtHopperId: TEdit;
    txtCoin: TEdit;
    Label5: TLabel;
    Label6: TLabel;
    btnEnableHopper: TButton;
    btnDisableHopper: TButton;
    btnEnablePaperTrading: TButton;
    btnDisablePaperTrading: TButton;
    txtWebhookURL: TEdit;
    chkWebhook: TCheckBox;
    txtHost: TEdit;
    Label8: TLabel;
    txtPort: TEdit;
    Label9: TLabel;
    txtValidationCode: TEdit;
    Label10: TLabel;
    Label11: TLabel;
    txtCertificate: TEdit;
    Label12: TLabel;
    txtPassword: TEdit;
    tabSignals: TTabSheet;
    txtSignalApiKey: TEdit;
    txtSignalApiSecret: TEdit;
    txtSignalId: TEdit;
    Label13: TLabel;
    Label14: TLabel;
    Label15: TLabel;
    txtSignalExchange: TEdit;
    txtSignalMarket: TEdit;
    Label16: TLabel;
    Label17: TLabel;
    cboSignalType: TComboBox;
    Label18: TLabel;
    cboSignalSend: TButton;
    cboSignalSendTest: TButton;
    procedure btnCancelOrderClick(Sender: TObject);
    procedure btnCreateHopperClick(Sender: TObject);
    procedure btnCreateWebhookClick(Sender: TObject);
    procedure btnDeleteAllOrdersClick(Sender: TObject);
    procedure btnDeleteHopperClick(Sender: TObject);
    procedure btnDeleteOrderClick(Sender: TObject);
    procedure btnDeleteWebhookClick(Sender: TObject);
    procedure btnDisableHopperClick(Sender: TObject);
    procedure btnDisablePaperTradingClick(Sender: TObject);
    procedure btnGetAllTickersClick(Sender: TObject);
    procedure btnGetExchangeClick(Sender: TObject);
    procedure btnGetHopperClick(Sender: TObject);
    procedure btnGetHoppersClick(Sender: TObject);
    procedure btnGetMarketTickerClick(Sender: TObject);
    procedure btnGetOpenOrderClick(Sender: TObject);
    procedure btnGetOpenOrdersClick(Sender: TObject);
    procedure btnGetOrderBookClick(Sender: TObject);
    procedure btnGetPositionClick(Sender: TObject);
    procedure btnGetTradeHistoryClick(Sender: TObject);
    procedure btnEnableHopperClick(Sender: TObject);
    procedure btnEnablePaperTradingClick(Sender: TObject);
    procedure cboPlaceLimitOrderClick(Sender: TObject);
    procedure cboPlaceMarketOrderClick(Sender: TObject);
    procedure cboSignalSendClick(Sender: TObject);
    procedure cboSignalSendTestClick(Sender: TObject);
    procedure chkWebhookClick(Sender: TObject);
    procedure cryptohopperWebhook(Sender: TObject; const aBody, aSignature: string);
  private
    procedure DoLog(const aValue: string);
    function GetCryptohopper: TsgcHTTP_Cryptohopper;
    function GetHopperId: string;
    function GetOrderId: string;
    function GetExchange: string;
    function GetPair: string;
  public
    { Public declarations }
  end;

var
  FRMCryptohopper: TFRMCryptohopper;

implementation

{$R *.dfm}

procedure TFRMCryptohopper.btnCancelOrderClick(Sender: TObject);
var
  vOrderId: string;
begin
  vOrderId := GetOrderId;

  DoLog(GetCryptohopper.CancelOrder(txtHopperId.Text, vOrderId));
end;

procedure TFRMCryptohopper.btnCreateHopperClick(Sender: TObject);
var
  vName: string;
begin
  vName := InputBox('Hopper Name', 'Set the Name', '');

  DoLog(GetCryptohopper.CreateHopper('{"name":"' + vName + '"}'));
end;

procedure TFRMCryptohopper.btnCreateWebhookClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.CreateWebhook(txtWebhookURL.text))
end;

procedure TFRMCryptohopper.btnDeleteAllOrdersClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.DeleteAllOrders(txtHopperId.Text));
end;

procedure TFRMCryptohopper.btnDeleteHopperClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.DeleteHopper(GetHopperId));
end;

procedure TFRMCryptohopper.btnDeleteOrderClick(Sender: TObject);
var
  vOrderId: string;
begin
  vOrderId := GetOrderId;

  DoLog(GetCryptohopper.DeleteOrder(txtHopperId.Text, vOrderId));
end;

procedure TFRMCryptohopper.btnDeleteWebhookClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.DeleteWebhook(txtWebhookURL.text))
end;

procedure TFRMCryptohopper.btnDisableHopperClick(Sender: TObject);
var
  oHopper: TsgcHTTPCTHopper;
  vId: string;
begin
  oHopper := TsgcHTTPCTHopper.Create;
  Try
    vId := GetHopperId;

    if GetCryptohopper.GetHopper(vId, oHopper) then
    begin
      oHopper.Enabled := 0;
      DoLog(GetCryptohopper.UpdateHopper(vId, oHopper));
    end;
  Finally
    FreeAndNil(oHopper);
  End;
end;

procedure TFRMCryptohopper.btnDisablePaperTradingClick(Sender: TObject);
var
  oHopper: TsgcHTTPCTHopper;
  vId: string;
begin
  oHopper := TsgcHTTPCTHopper.Create;
  Try
    vId := GetHopperId;

    if GetCryptohopper.GetHopper(vId, oHopper) then
    begin
      oHopper.Paper_Trading := 0;
      DoLog(GetCryptohopper.UpdateHopper(vId, oHopper));
    end;
  Finally
    FreeAndNil(oHopper);
  End;
end;

procedure TFRMCryptohopper.btnGetAllTickersClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetAllTickers(GetExchange));
end;

procedure TFRMCryptohopper.btnGetExchangeClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetExchange);
end;

procedure TFRMCryptohopper.btnGetHopperClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetHopper(GetHopperId));
end;

procedure TFRMCryptohopper.btnGetHoppersClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetHoppers);
end;

procedure TFRMCryptohopper.btnGetMarketTickerClick(Sender: TObject);
var
  vExchange: string;
  vPair: string;
begin
  vExchange := GetExchange;
  vPair := GetPair;

  DoLog(GetCryptohopper.GetMarketTicker(vExchange, vPair));
end;

procedure TFRMCryptohopper.btnGetOpenOrderClick(Sender: TObject);
var
  vOrderId: string;
begin
  vOrderId := GetOrderId;

  DoLog(GetCryptohopper.GetOpenOrder(txtHopperId.Text, vOrderId));
end;

procedure TFRMCryptohopper.btnGetOpenOrdersClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetOpenOrders(txtHopperId.Text));
end;

procedure TFRMCryptohopper.btnGetOrderBookClick(Sender: TObject);
var
  vExchange: string;
  vPair: string;
begin
  vExchange := GetExchange;
  vPair := GetPair;

  DoLog(GetCryptohopper.GetOrderBook(vExchange, vPair, '5'));
end;

procedure TFRMCryptohopper.btnGetPositionClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetPosition(GetHopperId));
end;

procedure TFRMCryptohopper.btnGetTradeHistoryClick(Sender: TObject);
begin
  DoLog(GetCryptohopper.GetTradeHistory(GetHopperId));
end;

procedure TFRMCryptohopper.btnEnableHopperClick(Sender: TObject);
var
  oHopper: TsgcHTTPCTHopper;
  vId: string;
begin
  oHopper := TsgcHTTPCTHopper.Create;
  Try
    vId := GetHopperId;

    if GetCryptohopper.GetHopper(vId, oHopper) then
    begin
      oHopper.Enabled := 1;
      DoLog(GetCryptohopper.UpdateHopper(vId, oHopper));
    end;
  Finally
    FreeAndNil(oHopper);
  End;
end;

procedure TFRMCryptohopper.btnEnablePaperTradingClick(Sender: TObject);
var
  oHopper: TsgcHTTPCTHopper;
  vId: string;
begin
  oHopper := TsgcHTTPCTHopper.Create;
  Try
    vId := GetHopperId;

    if GetCryptohopper.GetHopper(vId, oHopper) then
    begin
      oHopper.Paper_Trading := 1;
      DoLog(GetCryptohopper.UpdateHopper(vId, oHopper));
    end;
  Finally
    FreeAndNil(oHopper);
  End;
end;

procedure TFRMCryptohopper.cboPlaceLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPCTHOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboMarketSide.itemIndex = 0 then
    vSide := cthosBuy
  else
    vSide := cthosSell;

  DoLog(GetCryptohopper.PlaceLimitOrder(txtHopperId.Text, vSide, txtCoin.Text,
    StrToFloat(txtLimitOrderSize.Text, vFS), StrToFloat(txtLimitOrderPrice.Text, vFS)));
end;

procedure TFRMCryptohopper.cboPlaceMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPCTHOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboMarketSide.itemIndex = 0 then
    vSide := cthosBuy
  else
    vSide := cthosSell;

  DoLog(GetCryptohopper.PlaceMarketOrder(txtHopperId.Text, vSide, txtCoin.Text,
    StrToFloat(txtMarketOrderSize.Text, vFS)));
end;

procedure TFRMCryptohopper.cboSignalSendClick(Sender: TObject);
var
  oSignal: TsgcHTTPCTHSignal;
begin
  oSignal := TsgcHTTPCTHSignal.Create;
  Try
    oSignal.API_Key := txtSignalApiKey.Text;
    oSignal.API_Secret := txtSignalApiSecret.Text;
    oSignal.SignalId := txtSignalId.Text;
    oSignal.Exchange := txtSignalExchange.Text;
    oSignal.Market := txtSignalMarket.Text;
    case cboSignalType.ItemIndex of
      0: oSignal._Type := cthosBuy;
      1: oSignal._Type := cthosSell;
    end;

    DoLog(cryptohopper.SendSignal(oSignal));
  Finally
    oSignal.Free;
  End;
end;

procedure TFRMCryptohopper.cboSignalSendTestClick(Sender: TObject);
var
  oSignal: TsgcHTTPCTHSignal;
begin
  oSignal := TsgcHTTPCTHSignal.Create;
  Try
    oSignal.API_Key := txtSignalApiKey.Text;
    oSignal.API_Secret := txtSignalApiSecret.Text;
    oSignal.SignalId := txtSignalId.Text;
    oSignal.Exchange := txtSignalExchange.Text;
    oSignal.Market := txtSignalMarket.Text;
    case cboSignalType.ItemIndex of
      0: oSignal._Type := cthosBuy;
      1: oSignal._Type := cthosSell;
    end;

    DoLog(cryptohopper.SendTestSignal(oSignal));
  Finally
    oSignal.Free;
  End;
end;

procedure TFRMCryptohopper.chkWebhookClick(Sender: TObject);
begin
  if chkWebhook.Checked then
    GetCryptohopper.StartWebhook
  else
    GetCryptohopper.StopWebhook;
end;

procedure TFRMCryptohopper.cryptohopperWebhook(Sender: TObject; const aBody,
    aSignature: string);
begin
  DoLog(aBody);
end;

procedure TFRMCryptohopper.DoLog(const aValue: string);
begin
  memoLog.Lines.Add(aValue);
end;

function TFRMCryptohopper.GetCryptohopper: TsgcHTTP_Cryptohopper;
begin
  cryptohopper.CryptohopperOptions.OAuth2.ClientId := txtClientId.Text;
  cryptohopper.CryptohopperOptions.OAuth2.ClientSecret := txtClientSecret.Text;
  cryptohopper.CryptohopperOptions.OAuth2.LocalIP := txtLocalIP.Text;
  cryptohopper.CryptohopperOptions.OAuth2.LocalPort :=
    StrToInt(txtLocalPort.Text);

  cryptohopper.CryptohopperOptions.Webhook.Enabled := chkWebhook.Checked;
  cryptohopper.CryptohopperOptions.Webhook.Host := txtHost.Text;
  cryptohopper.CryptohopperOptions.Webhook.Port := StrToInt(txtPort.Text);
  cryptohopper.CryptohopperOptions.Webhook.ValidationCode := txtValidationCode.Text;
  cryptohopper.CryptohopperOptions.Webhook.SSLOptions.CertFile := txtCertificate.Text;
  cryptohopper.CryptohopperOptions.Webhook.SSLOptions.KeyFile := txtCertificate.Text;
  cryptohopper.CryptohopperOptions.Webhook.SSLOptions.RootCertFile := txtCertificate.Text;
  cryptohopper.CryptohopperOptions.Webhook.SSLOptions.Password := txtPassword.Text;

  Result := cryptohopper;
end;

function TFRMCryptohopper.GetExchange: string;
begin
  Result := InputBox('Exchange Name', 'Set the Exchange Name', '');
end;

function TFRMCryptohopper.GetHopperId: string;
begin
  Result := InputBox('Hopper Id', 'Set the Hopper Id', '');
end;

function TFRMCryptohopper.GetOrderId: string;
begin
  Result := InputBox('Order Id', 'Set the Order Id', '');
end;

function TFRMCryptohopper.GetPair: string;
begin
  Result := InputBox('Pair Name', 'Set the Pair Name', '');
end;

end.
```

