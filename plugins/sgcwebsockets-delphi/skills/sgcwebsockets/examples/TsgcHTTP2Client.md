# TsgcHTTP2Client - Example

Full source of `FHTTP2_Client.pas` from the **20.HTTP_Protocol/01.HTTP2_Server_And_Client** demo, which uses `TsgcHTTP2Client`.

API reference: [TsgcHTTP2Client](../reference/api/TsgcHTTP2Client.md)
Source demo: `20.HTTP_Protocol/01.HTTP2_Server_And_Client` (file `FHTTP2_Client.pas`)

```pascal
unit FHTTP2_Client;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, ComCtrls,
  sgcIdHTTP, sgcHTTP, sgcHTTP2_Client, sgcBase_Classes, sgcTCP_Classes,
  sgcTCP_Client, sgcHTTP2_Types, sgcIdAuthentication, sgcWebSocket_Classes,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcBase_Helpers, sgcHTTP2_Frame, sgcWebSocket_Types, Menus, Threading,
  sgcSocket_Classes;

type
  TFRMHTTP2_Client = class(TForm)
    PageControl1: TPageControl;
    tabPerformance: TTabSheet;
    imgHTTP2: TImage;
    imgHTTP: TImage;
    btnStartPerformance: TButton;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    tabLatency: TTabSheet;
    imgGophertiles: TImage;
    btnGoHTTP2_0_Latency: TButton;
    tabRequest: TTabSheet;
    txtURL: TEdit;
    cboMethod: TComboBox;
    btnExecuteRequest: TButton;
    memoResponseHeaders: TMemo;
    memoRequest: TMemo;
    memoResponseBody: TMemo;
    Label16: TLabel;
    Label17: TLabel;
    btnGoHTTP2_30_Latency: TButton;
    btnGoHTTP2_200_Latency: TButton;
    btnGoHTTP2_1000_Latency: TButton;
    btnGoHTTP1_0_Latency: TButton;
    btnGoHTTP1_30_Latency: TButton;
    btnGoHTTP1_200_Latency: TButton;
    btnGoHTTP1_1000_Latency: TButton;
    Label18: TLabel;
    PageControl2: TPageControl;
    tabResponse: TTabSheet;
    tabRequestLog: TTabSheet;
    memoLog: TMemo;
    tabHTTPBIN: TTabSheet;
    btnMethodGET: TButton;
    btnMethodDELETE: TButton;
    btnMethodPATCH: TButton;
    btnMethodPOST: TButton;
    pageHTTPBIN: TPageControl;
    tabHTTPMethods: TTabSheet;
    btnMethodPUT: TButton;
    Label19: TLabel;
    Label20: TLabel;
    Label21: TLabel;
    Label22: TLabel;
    Label23: TLabel;
    memoHTTPBIN: TMemo;
    tabAuthorization: TTabSheet;
    btnAuthBasicGET: TButton;
    Label24: TLabel;
    txtAuthUser: TEdit;
    txtAuthPassword: TEdit;
    btnAuthBearerGET: TButton;
    Label25: TLabel;
    txtBearerToken: TEdit;
    tabStatusCodes: TTabSheet;
    btnStatusCodesDELETE: TButton;
    Label26: TLabel;
    btnStatusCodesGET: TButton;
    Label27: TLabel;
    btnStatusCodesPATCH: TButton;
    Label28: TLabel;
    btnStatusCodesPOST: TButton;
    Label29: TLabel;
    btnStatusCodesPUT: TButton;
    Label30: TLabel;
    txtStatusCode: TEdit;
    Label31: TLabel;
    tabRequestInspection: TTabSheet;
    btnRequestInspectionHeadersGET: TButton;
    Label32: TLabel;
    btnRequestInspectionIpGET: TButton;
    Label33: TLabel;
    btnRequestInspectionUserAgentGET: TButton;
    Label34: TLabel;
    tabResponseInspection: TTabSheet;
    btnResponseInspectionHeadersGET: TButton;
    txtResponseHeadersGET: TEdit;
    Label35: TLabel;
    btnResponseInspectionHeadersPOST: TButton;
    Label36: TLabel;
    txtResponseHeadersPOST: TEdit;
    tabResponseFormats: TTabSheet;
    btnResponseFormatsDenyGET: TButton;
    Label37: TLabel;
    btnResponseFormatsUTF8GET: TButton;
    Label38: TLabel;
    btnResponseFormatsHTMLGET: TButton;
    Label39: TLabel;
    btnResponseFormatsJSONGET: TButton;
    Label40: TLabel;
    btnResponseFormatsRobotsGET: TButton;
    Label41: TLabel;
    btnResponseFormatsXMLGET: TButton;
    Label42: TLabel;
    tabDynamicData: TTabSheet;
    btnDynamicDataBase64GET: TButton;
    Label43: TLabel;
    btnDynamicDataBytesGET: TButton;
    Label44: TLabel;
    btnDynamicDataDelayGET: TButton;
    Label45: TLabel;
    btnDynamicDataLinksGET: TButton;
    Label46: TLabel;
    btnDynamicDataRangeGET: TButton;
    Label47: TLabel;
    btnDynamicDataStreamBytesGET: TButton;
    Label48: TLabel;
    btnDynamicDataStreamGET: TButton;
    Label49: TLabel;
    btnDynamicDataUUIDGET: TButton;
    Label50: TLabel;
    tabCookies: TTabSheet;
    btnCookiesGET: TButton;
    Label51: TLabel;
    btnCookiesDeleteGET: TButton;
    Label52: TLabel;
    btnCookiesSetGET: TButton;
    Label53: TLabel;
    btnCookiesRedirectGET: TButton;
    Label54: TLabel;
    tabImages: TTabSheet;
    btnImagesJPEG: TButton;
    Label55: TLabel;
    btnImagesPNG: TButton;
    Label56: TLabel;
    btnImagesSVG: TButton;
    Label57: TLabel;
    btnImagesWEBP: TButton;
    Label58: TLabel;
    Image1: TImage;
    tabRedirects: TTabSheet;
    btnRedirectsAbsoluteGET: TButton;
    Label59: TLabel;
    btnRedirectsRedirectToGET: TButton;
    Label60: TLabel;
    btnRedirectsGET: TButton;
    Label61: TLabel;
    btnRedirectsRelativeDirectGET: TButton;
    Label62: TLabel;
    tabAnything: TTabSheet;
    btnAnythingGET: TButton;
    Label63: TLabel;
    btnAnythingPATCH: TButton;
    Label64: TLabel;
    btnAnythingPOST: TButton;
    Label65: TLabel;
    btnAnythingPUT: TButton;
    Label66: TLabel;
    btnAnythingDELETE: TButton;
    Label67: TLabel;
    btnResponseFormatsDeflateGET: TButton;
    Label68: TLabel;
    btnResponseFormatsGzipGET: TButton;
    Label69: TLabel;
    MainMenu1: TMainMenu;
    Application1: TMenuItem;
    Exit1: TMenuItem;
    N1: TMenuItem;
    h2specd1: TMenuItem;
    procedure btnAnythingDELETEClick(Sender: TObject);
    procedure btnAnythingGETClick(Sender: TObject);
    procedure btnAnythingPATCHClick(Sender: TObject);
    procedure btnAnythingPOSTClick(Sender: TObject);
    procedure btnAnythingPUTClick(Sender: TObject);
    procedure btnAuthBasicGETClick(Sender: TObject);
    procedure btnAuthBearerGETClick(Sender: TObject);
    procedure btnCookiesDeleteGETClick(Sender: TObject);
    procedure btnCookiesGETClick(Sender: TObject);
    procedure btnCookiesRedirectGETClick(Sender: TObject);
    procedure btnCookiesSetGETClick(Sender: TObject);
    procedure btnDynamicDataBase64GETClick(Sender: TObject);
    procedure btnDynamicDataBytesGETClick(Sender: TObject);
    procedure btnDynamicDataDelayGETClick(Sender: TObject);
    procedure btnDynamicDataLinksGETClick(Sender: TObject);
    procedure btnDynamicDataRangeGETClick(Sender: TObject);
    procedure btnDynamicDataStreamBytesGETClick(Sender: TObject);
    procedure btnDynamicDataStreamGETClick(Sender: TObject);
    procedure btnDynamicDataUUIDGETClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnExecuteRequestClick(Sender: TObject);
    procedure btnStartPerformanceClick(Sender: TObject);
    procedure btnGoHTTP2_0_LatencyClick(Sender: TObject);
    procedure btnGoHTTP2_1000_LatencyClick(Sender: TObject);
    procedure btnGoHTTP2_200_LatencyClick(Sender: TObject);
    procedure btnGoHTTP2_30_LatencyClick(Sender: TObject);
    procedure btnGoHTTP1_0_LatencyClick(Sender: TObject);
    procedure btnGoHTTP1_30_LatencyClick(Sender: TObject);
    procedure btnGoHTTP1_200_LatencyClick(Sender: TObject);
    procedure btnGoHTTP1_1000_LatencyClick(Sender: TObject);
    procedure btnImagesJPEGClick(Sender: TObject);
    procedure btnImagesPNGClick(Sender: TObject);
    procedure btnImagesSVGClick(Sender: TObject);
    procedure btnImagesWEBPClick(Sender: TObject);
    procedure btnMethodDELETEClick(Sender: TObject);
    procedure btnMethodGETClick(Sender: TObject);
    procedure btnMethodPATCHClick(Sender: TObject);
    procedure btnMethodPOSTClick(Sender: TObject);
    procedure btnMethodPUTClick(Sender: TObject);
    procedure btnRedirectsAbsoluteGETClick(Sender: TObject);
    procedure btnRedirectsGETClick(Sender: TObject);
    procedure btnRedirectsRedirectToGETClick(Sender: TObject);
    procedure btnRedirectsRelativeDirectGETClick(Sender: TObject);
    procedure btnRequestInspectionHeadersGETClick(Sender: TObject);
    procedure btnRequestInspectionIpGETClick(Sender: TObject);
    procedure btnRequestInspectionUserAgentGETClick(Sender: TObject);
    procedure btnResponseFormatsDeflateGETClick(Sender: TObject);
    procedure btnResponseFormatsDenyGETClick(Sender: TObject);
    procedure btnResponseFormatsGzipGETClick(Sender: TObject);
    procedure btnResponseFormatsHTMLGETClick(Sender: TObject);
    procedure btnResponseFormatsJSONGETClick(Sender: TObject);
    procedure btnResponseFormatsRobotsGETClick(Sender: TObject);
    procedure btnResponseFormatsUTF8GETClick(Sender: TObject);
    procedure btnResponseFormatsXMLGETClick(Sender: TObject);
    procedure btnResponseInspectionHeadersGETClick(Sender: TObject);
    procedure btnResponseInspectionHeadersPOSTClick(Sender: TObject);
    procedure btnStatusCodesDELETEClick(Sender: TObject);
    procedure btnStatusCodesGETClick(Sender: TObject);
    procedure btnStatusCodesPATCHClick(Sender: TObject);
    procedure btnStatusCodesPOSTClick(Sender: TObject);
    procedure btnStatusCodesPUTClick(Sender: TObject);
    procedure cboMethodChange(Sender: TObject);
    procedure h2specd1Click(Sender: TObject);
    // request
  private
    FClient_Request: TsgcHTTP2Client;
    procedure OnHTTP2ResponseEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const Request: TsgcHTTP2RequestProperty; const
        Response: TsgcHTTP2ResponseProperty);
    procedure OnHTTP2ConnectEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient);
    procedure OnHTTP2DisconnectEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient);
    procedure OnHTTP2ExceptionEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const E: Exception);
    // performance
  private
    FClient_Performance: TsgcHTTP2Client;
    function GetPerformanceServerURL: String;
    procedure OnPerformanceHTTP2ResponseEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const Request: TsgcHTTP2RequestProperty; const
        Response: TsgcHTTP2ResponseProperty);
    procedure OnPerformanceHTTP2PendingRequestsEvent(Sender: TObject; const
        Connection: TsgcHTTP2ConnectionClient; var aReconnect, aClear: Boolean);
    procedure DoTestPerformance;
    // latency
  private
    FClient_Latency: TsgcHTTP2Client;
    function GetLatencyServerURL: String;
    procedure DoGoLatencyHTTP2(const aLatency: Integer);
    procedure DoGoLatencyHTTP1(const aLatency: Integer);
    procedure OnLatencyHTTP2ResponseEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const Request: TsgcHTTP2RequestProperty; const
        Response: TsgcHTTP2ResponseProperty);
    procedure OnLatencyHTTP2PendingRequests(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; var aReconnect, aClear: Boolean);
    // HTTPBIN.ORG
  private
    FClient_HTTPBIN: TsgcHTTP2Client;
    function GetClientHTTPBIN: TsgcHTTP2Client;
    procedure OnHTTP2HTTPBinResponseEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const Request: TsgcHTTP2RequestProperty; const
        Response: TsgcHTTP2ResponseProperty);
    procedure OnHTTP2HTTPBINAuthorizationEvent(Sender: TObject; const Connection:
        TsgcHTTP2ConnectionClient; const AuthType, AuthData: string; var UserName,
        Password, aToken: string; var Handled: Boolean);
    procedure DoHTTPBIN(aMethod: Th2Methods; aParameters: String; aSource: String =
        '');
  end;

  THTTP1_Thread = class(TThread)
  private
    FURL: String;
  public
    procedure Execute; override;
  public
    property URL: String read FURL write FURL;
  end;


var
  FRMHTTP2_Client: TFRMHTTP2_Client;

implementation

uses
  StrUtils, JPEG;

{$R *.dfm}

procedure TFRMHTTP2_Client.btnAnythingDELETEClick(Sender: TObject);
begin
  DoHTTPBIN(h2meDELETE, '/anything');
end;

procedure TFRMHTTP2_Client.btnAnythingGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/anything');
end;

procedure TFRMHTTP2_Client.btnAnythingPATCHClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePATCH, '/anything');
end;

procedure TFRMHTTP2_Client.btnAnythingPOSTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePOST, '/anything');
end;

procedure TFRMHTTP2_Client.btnAnythingPUTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePUT, '/anything');
end;

procedure TFRMHTTP2_Client.btnAuthBasicGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, Format('/basic-auth/%s/%s', [txtAuthUser.Text, txtAuthPassword.Text]));
end;

procedure TFRMHTTP2_Client.btnAuthBearerGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/bearer');
end;

procedure TFRMHTTP2_Client.btnCookiesDeleteGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/cookies/delete?freeform=' + InputBox('Cookies', 'Value', 'sgc_cookies'));
end;

procedure TFRMHTTP2_Client.btnCookiesGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/cookies');
end;

procedure TFRMHTTP2_Client.btnCookiesRedirectGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/cookies/set/' + InputBox('Cookies', 'Name', 'sgc_name') + '/' + InputBox('Cookies', 'Value', 'sgc_value'));
end;

procedure TFRMHTTP2_Client.btnCookiesSetGETClick(Sender: TObject);
var
  vValue: String;
begin
  vValue := InputBox('Cookies', 'Value', 'sgc_cookies');
  GetClientHTTPBIN.Request.AddCookie('freeform', vValue);
  DoHTTPBin(h2meGET, '/cookies/set?freeform=' + vValue);
end;

procedure TFRMHTTP2_Client.btnDynamicDataBase64GETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/base64/' + EncodeBase64(InputBox('Base64', 'Value', 'HTTPBIN is awesome')));
end;

procedure TFRMHTTP2_Client.btnDynamicDataBytesGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/bytes/' + InputBox('Bytes', 'Value', '10'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataDelayGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/delay/' + InputBox('Seconds', 'Value', '10'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataLinksGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGet, '/links/' + InputBox('Links', 'Value', '10') + '/' + InputBox('Offset', 'Value', '5'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataRangeGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/range/' + InputBox('Num Bytes', 'Value', '1024'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataStreamBytesGETClick(Sender: TObject);
begin
  DoHTTPBin(h2meGET, '/stream-bytes/' + InputBox('Num Bytes', 'Value', '4096'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataStreamGETClick(Sender: TObject);
begin
  DoHTTPBIn(h2meGET, '/stream/' + InputBox('JSON Responses', 'Value', '10'));
end;

procedure TFRMHTTP2_Client.btnDynamicDataUUIDGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/uuid');
end;

procedure TFRMHTTP2_Client.FormCreate(Sender: TObject);
//var
//  page: integer;
begin
//  for page := 0 to PageControl1.PageCount - 1 do
//    PageControl1.Pages[page].TabVisible := false;
//  tabHTTPBIN.Visible := True;
end;

procedure TFRMHTTP2_Client.btnExecuteRequestClick(Sender: TObject);
var
  oSource: TStringStream;
begin
  if not Assigned(FClient_Request) then
  begin
    FClient_Request := TsgcHTTP2Client.Create(self);
    FClient_Request.OnHTTP2Connect := OnHTTP2ConnectEvent;
    FClient_Request.OnHTTP2Disconnect := OnHTTP2DisconnectEvent;
    FClient_Request.OnHTTP2Exception := OnHTTP2ExceptionEvent;
    FClient_Request.OnHTTP2Response := OnHTTP2ResponseEvent;
  end;
  
  // wait the client has disconnected to avoid thread error
  While FClient_Request.Active do
    sleep(1);

  case cboMethod.ItemIndex of
    0:
      begin
        memoResponseBody.Lines.Text := FClient_Request.Get(txtURL.Text);
        memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
        FClient_Request.Disconnect;
      end;
    1:
      begin
        oSource := TStringStream.Create(memoRequest.Lines.Text);
        Try
          memoResponseBody.Lines.Text := FClient_Request.Post(txtURL.Text, oSource);
          memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
          FClient_Request.Disconnect;
        Finally
          oSource.Free;
          memoRequest.Lines.Clear;
        end;
      end;
    2:
      begin
        oSource := TStringStream.Create(memoRequest.Lines.Text);
        Try
          memoResponseBody.Lines.Text := FClient_Request.Put(txtURL.Text, oSource);
          memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
          FClient_Request.Disconnect;
        Finally
          oSource.Free;
          memoRequest.Lines.Clear;
        end;
      end;
    3: FClient_Request.Delete(txtURL.Text);
    4:
      begin
        oSource := TStringStream.Create(memoRequest.Lines.Text);
        Try
          memoResponseBody.Lines.Text := FClient_Request.Patch(txtURL.Text, oSource);
          memoResponseHeaders.Lines.Text := FClient_Request.Response.Headers.Text;
          FClient_Request.Disconnect;
        Finally
          oSource.Free;
          memoRequest.Lines.Clear;
        end;
      end;
  end;

  memoRequest.Lines.Clear;
end;

procedure TFRMHTTP2_Client.btnStartPerformanceClick(Sender: TObject);
begin
  DoTestPerformance;
end;

procedure TFRMHTTP2_Client.btnGoHTTP2_0_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP2(0);
end;

procedure TFRMHTTP2_Client.btnGoHTTP2_1000_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP2(1000);
end;

procedure TFRMHTTP2_Client.btnGoHTTP2_200_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP2(200);
end;

procedure TFRMHTTP2_Client.btnGoHTTP2_30_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP2(30);
end;

procedure TFRMHTTP2_Client.btnGoHTTP1_0_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP1(0);
end;

procedure TFRMHTTP2_Client.btnGoHTTP1_30_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP1(30);
end;

procedure TFRMHTTP2_Client.btnGoHTTP1_200_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP1(200);
end;

procedure TFRMHTTP2_Client.btnGoHTTP1_1000_LatencyClick(Sender: TObject);
begin
  DoGoLatencyHTTP1(1000);
end;

procedure TFRMHTTP2_Client.btnImagesJPEGClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/image/jpeg');
end;

procedure TFRMHTTP2_Client.btnImagesPNGClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/image/png');
end;

procedure TFRMHTTP2_Client.btnImagesSVGClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/image/svg');
end;

procedure TFRMHTTP2_Client.btnImagesWEBPClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/image/webp');
end;

procedure TFRMHTTP2_Client.btnMethodDELETEClick(Sender: TObject);
begin
  DoHTTPBIN(h2meDelete, '/delete');
end;

procedure TFRMHTTP2_Client.btnMethodGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGet, '/get');
end;

procedure TFRMHTTP2_Client.btnMethodPATCHClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePatch, '/patch');
end;

procedure TFRMHTTP2_Client.btnMethodPOSTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePost, '/post');
end;

procedure TFRMHTTP2_Client.btnMethodPUTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePut, '/put');
end;

procedure TFRMHTTP2_Client.btnRedirectsAbsoluteGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/absolute-redirect/' + InputBox('Redirects', 'Value', '5'));
end;

procedure TFRMHTTP2_Client.btnRedirectsGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/redirect/' + InputBox('Redirects', 'Value', '5'));
end;

procedure TFRMHTTP2_Client.btnRedirectsRedirectToGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/redirect-to?url=' + InputBox('URL', 'Value', 'https://www.google.es') + '&status_code=' + InputBox('Status Code', 'Value', '302'));
end;

procedure TFRMHTTP2_Client.btnRedirectsRelativeDirectGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/relative-redirect/' + InputBox('Redirects', 'Value', '5'));
end;

procedure TFRMHTTP2_Client.btnRequestInspectionHeadersGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/headers');
end;

procedure TFRMHTTP2_Client.btnRequestInspectionIpGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/ip');
end;

procedure TFRMHTTP2_Client.btnRequestInspectionUserAgentGETClick(Sender:
    TObject);
begin
  DoHTTPBIN(h2meGET, '/user-agent');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsDeflateGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/deflate');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsDenyGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/deny');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsGzipGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/gzip');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsHTMLGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/html');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsJSONGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/json');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsRobotsGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/robots.txt');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsUTF8GETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/encoding/utf8');
end;

procedure TFRMHTTP2_Client.btnResponseFormatsXMLGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, '/xml');
end;

procedure TFRMHTTP2_Client.btnResponseInspectionHeadersGETClick(Sender:
    TObject);
begin
  DoHTTPBIN(h2meGET, '/response-headers?freeform=' + txtResponseHeadersGET.Text);
end;

procedure TFRMHTTP2_Client.btnResponseInspectionHeadersPOSTClick(Sender:
    TObject);
begin
  DoHTTPBIN(h2mePOST, '/response-headers?freeform=' + txtResponseHeadersPOST.Text);
end;

procedure TFRMHTTP2_Client.btnStatusCodesDELETEClick(Sender: TObject);
begin
  DoHTTPBIN(h2meDELETE, Format('/status/%d', [StrToInt(txtStatusCode.Text)]));
end;

procedure TFRMHTTP2_Client.btnStatusCodesGETClick(Sender: TObject);
begin
  DoHTTPBIN(h2meGET, Format('/status/%d', [StrToInt(txtStatusCode.Text)]));
end;

procedure TFRMHTTP2_Client.btnStatusCodesPATCHClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePATCH, Format('/status/%d', [StrToInt(txtStatusCode.Text)]));
end;

procedure TFRMHTTP2_Client.btnStatusCodesPOSTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePOST, Format('/status/%d', [StrToInt(txtStatusCode.Text)]));
end;

procedure TFRMHTTP2_Client.btnStatusCodesPUTClick(Sender: TObject);
begin
  DoHTTPBIN(h2mePUT, Format('/status/%d', [StrToInt(txtStatusCode.Text)]));
end;

procedure TFRMHTTP2_Client.cboMethodChange(Sender: TObject);
begin
  case cboMethod.ItemIndex of
    1, 2, 4: memoRequest.Enabled := True;
    else
      memoRequest.Enabled := False;
  end;
end;

procedure TFRMHTTP2_Client.DoGoLatencyHTTP1(const aLatency: Integer);
var
  oHTTP: TsgcHTTP1Client;
  x, y: Integer;
  vCachebust: string;
  oStream: TMemoryStream;
  oJPEG: TJPEGImage;
begin
  imgGophertiles.Picture.Graphic := nil;

  oHTTP := TsgcHTTP1Client.Create(nil);
  Try
    oHTTP.Request.Accept := 'image/*,*/*;q=0.8';
    vCacheBust := FormatDateTime('yyyymmddhhnnsszzz', Now);
    for y := 0 to 11 do
    begin
      for x := 0 to 14 do
      begin
        oStream := TMemoryStream.Create;
        Try
          oHTTP.Get(GetLatencyServerURL + '/gophertiles?x=' + IntToStr(x) + '&y=' + IntToStr(y) + '&cachebust=' + vCachebust + '&latency=' + IntToStr(aLatency), oStream);

          oJPEG := TJPEGImage.Create;
          oStream.Position := 0;
          oJPEG.LoadFromStream(oStream);

          TThread.Queue(nil,
          procedure
          begin
            if Assigned(imgGophertiles) then
            begin
              imgGophertiles.Canvas.Draw(x * 32, y * 32, oJPEG);
              Application.ProcessMessages;
            end;
          end);
        Finally
          oStream.Free;
        End;
      end;
    end;
  Finally
    oHTTP.Free;
  End;
end;

procedure TFRMHTTP2_Client.DoGoLatencyHTTP2(const aLatency: Integer);
var
  x, y: Integer;
  vCachebust: string;
begin
  imgGophertiles.Picture.Graphic := nil;
  if Assigned(FClient_Latency) then
    FClient_Latency.Active := False;
  FClient_Latency := TsgcHTTP2Client.Create(self);
  FClient_Latency.OnHTTP2Response := OnLatencyHTTP2ResponseEvent;
  FClient_Latency.OnHTTP2PendingRequests := OnLatencyHTTP2PendingRequests;
  FClient_Latency.Request.Accept := 'image/*,*/*;q=0.8';
  FClient_Latency.WatchDog.Enabled := True;
  vCacheBust := FormatDateTime('yyyymmddhhnnsszzz', Now);
  for y := 0 to 11 do
  begin
    for x := 0 to 14 do
      FClient_Latency.GetAsync(GetLatencyServerURL + '/gophertiles?x=' + IntToStr(x) + '&y=' + IntToStr(y) + '&cachebust=' + vCachebust + '&latency=' + IntToStr(aLatency));
  end;
end;

procedure TFRMHTTP2_Client.DoHTTPBIN(aMethod: Th2Methods; aParameters: String;
    aSource: String = '');
var
  vURL: String;
  oStream: TStringStream;
begin
  vURL := 'https://httpbin.org' + aParameters;

  oStream := TStringStream.Create(aSource);
  Try
    case aMethod of
      h2meGet: GetClientHTTPBIN.GetAsync(vURL);
      h2mePost: GetClientHTTPBIN.PostAsync(vURL, oStream);
      h2mePut: GetClientHTTPBIN.PutAsync(vURL, oStream);
      h2meDelete: GetClientHTTPBIN.DeleteAsync(vURL);
      h2mePatch: GetClientHTTPBIN.PatchAsync(vURL, oStream);
    end;
  Finally
    oStream.Free;
  End;
end;

procedure TFRMHTTP2_Client.DoTestPerformance;
var
  oHTTP1: THTTP1_Thread;
  i: integer;
begin
  // ... http1
  oHTTP1 := THTTP1_Thread.Create(True);
  oHTTP1.URL := GetPerformanceServerURL;
  oHTTP1.FreeOnTerminate := True;
  oHTTP1.Start;

  // ... http2
  imgHTTP2.Picture.Graphic := nil;
  FreeAndNil(FClient_Performance);
  FClient_Performance := TsgcHTTP2Client.Create(self);
  FClient_Performance.OnHTTP2Response := OnPerformanceHTTP2ResponseEvent;
  FClient_Performance.OnHTTP2PendingRequests := OnPerformanceHTTP2PendingRequestsEvent;
  FClient_Performance.Request.Accept := 'image/*,*/*;q=0.8';
  for i := 1 to 100 do
    FClient_Performance.GetAsync(GetPerformanceServerURL + '/demo/img/http_test/h_' + Format('%.2d', [i]) + '.jpg');
end;

function TFRMHTTP2_Client.GetClientHTTPBIN: TsgcHTTP2Client;
begin
  if not Assigned(FClient_HTTPBIN) then
  begin
    FClient_HTTPBIN := TsgcHTTP2Client.Create(self);
    FClient_HTTPBIN.OnHTTP2Response := OnHTTP2HTTPBinResponseEvent;
    FClient_HTTPBIN.OnHTTP2Authorization := OnHTTP2HTTPBINAuthorizationEvent;
  end;
  Result := FClient_HTTPBIN;
end;

function TFRMHTTP2_Client.GetLatencyServerURL: String;
begin
  result := 'https://127.0.0.1:5450';
end;

function TFRMHTTP2_Client.GetPerformanceServerURL: String;
begin
  result := 'https://127.0.0.1:5450';
end;

procedure TFRMHTTP2_Client.h2specd1Click(Sender: TObject);
var
  oClient: TsgcHTTP2Client;
  i: Integer;
begin
  for i := 30000 to 30056 do
  begin
    oClient := TsgcHTTP2Client.Create(self);
    Try
      oClient.NotifyEvents := neNoSync;
      oClient.GetAsync('https://127.0.0.1:' + IntToStr(i) + '/');
    Finally
//      oClient.Free;
    End;
  end;
end;

procedure TFRMHTTP2_Client.OnHTTP2ExceptionEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient; const E: Exception);
begin
  memoLog.Lines.Add('#exception: ' + E.Message);
end;

procedure TFRMHTTP2_Client.OnHTTP2HTTPBinResponseEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient; const Request:
    TsgcHTTP2RequestProperty; const Response: TsgcHTTP2ResponseProperty);
var
  vHeaders: String;
  vBody: String;
  oJPEG: TJPEGImage;
begin
  vHeaders := Response.Headers.Text;
  if Request.URL = '/encoding/utf8' then
    vBody := Response.DataUTF8
  else
    vBody := Response.DataString;
  if Response.Headers.Values['content-type'] = 'image/jpeg' then
  begin
    oJPEG := TJPEGImage.Create;
    Response.Data.Position := 0;
    oJPEG.LoadFromStream(Response.Data);
  end
  else
    oJPEG := nil;

  memoHTTPBIN.Lines.Text := vHeaders + #13#10 + vBody;
  if Assigned(oJPEG) then
  begin
    Image1.Canvas.Draw(0, 0, oJPEG);
    FreeAndNil(oJPEG);
  end;
end;

procedure TFRMHTTP2_Client.OnHTTP2ConnectEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient);
begin
  memoLog.Lines.Add('#connected');
end;

procedure TFRMHTTP2_Client.OnHTTP2DisconnectEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient);
begin
  memoLog.Lines.Add('#disconnected');
end;

procedure TFRMHTTP2_Client.OnHTTP2HTTPBINAuthorizationEvent(Sender: TObject;
    const Connection: TsgcHTTP2ConnectionClient; const AuthType, AuthData:
    string; var UserName, Password, aToken: string; var Handled: Boolean);
begin
  if AuthType = 'Basic' then
  begin
    UserName := InputBox(AuthData, 'Username', txtAuthUser.text);
    Password := InputBox(AuthData, 'Password', txtAuthPassword.text);
  end
  else if AuthType = 'Bearer' then
  begin
    aToken := txtBearerToken.Text;
  end;
end;

procedure TFRMHTTP2_Client.OnLatencyHTTP2PendingRequests(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient; var aReconnect, aClear: Boolean);
begin
  aReconnect := True;
  aClear := False;
end;

procedure TFRMHTTP2_Client.OnHTTP2ResponseEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient; const Request:
    TsgcHTTP2RequestProperty; const Response: TsgcHTTP2ResponseProperty);
begin
  memoResponseHeaders.Lines.Text := Response.Headers.Text;
  memoResponseBody.Lines.Text := Response.DataString;
  Connection.Close;
end;

procedure TFRMHTTP2_Client.OnLatencyHTTP2ResponseEvent(Sender: TObject; const
    Connection: TsgcHTTP2ConnectionClient; const Request:
    TsgcHTTP2RequestProperty; const Response: TsgcHTTP2ResponseProperty);
var
  oJPEG: TJPEGImage;
  oList: TStringList;
  x, y: Integer;
begin
  oJPEG := TJPEGImage.Create;
  oJPEG.LoadFromStream(Response.Data);
  oList := TStringList.Create;
  Try
    oList.Delimiter := '&';
    oList.StrictDelimiter := True;
    oList.DelimitedText := StringReplace(Request.URL, '/gophertiles?', '', []);
    x := StrToInt(oList.Values['x']);
    y := StrToInt(oList.Values['y']);
  Finally
    oList.Free;
  End;

  if Assigned(imgHTTP2) then
  begin
    imgGophertiles.Canvas.Draw(x * 32, y * 32, oJPEG);
    oJPEG.Free;
  end;
end;

procedure TFRMHTTP2_Client.OnPerformanceHTTP2PendingRequestsEvent(Sender:
    TObject; const Connection: TsgcHTTP2ConnectionClient; var aReconnect,
    aClear: Boolean);
begin
  aReconnect := True;
  aClear := False;
end;

procedure TFRMHTTP2_Client.OnPerformanceHTTP2ResponseEvent(Sender: TObject;
    const Connection: TsgcHTTP2ConnectionClient; const Request:
    TsgcHTTP2RequestProperty; const Response: TsgcHTTP2ResponseProperty);
var
  oJPEG: TJPEGImage;
  vURL: String;
  vNum: Integer;
  vCol, vRow: Integer;
begin
  oJPEG := TJPEGImage.Create;
  oJPEG.LoadFromStream(Response.Data);
  oJPEG.Scale := jsHalf;
  vURL := Request.URL;
  vURL := LeftStr(StringReplace(vURL, '/demo/img/http_test/h_', '', []), 3);
  vURL := StringReplace(vURL, '.', '', []);
  TryStrToInt(vURL, vNum);
  vCol := 0;
  vRow := 0;
  if vNum < 11 then
  begin
    vCol := vNum - 1;
    vRow := 0;
  end
  else if vNum < 21 then
  begin
    vCol := vNum - 11;
    vRow := 1;
  end
  else if vNum < 31 then
  begin
    vCol := vNum - 21;
    vRow := 2;
  end
  else if vNum < 41 then
  begin
    vCol := vNum - 31;
    vRow := 3;
  end
  else if vNum < 51 then
  begin
    vCol := vNum - 41;
    vRow := 4;
  end
  else if vNum < 61 then
  begin
    vCol := vNum - 51;
    vRow := 5;
  end
  else if vNum < 71 then
  begin
    vCol := vNum - 61;
    vRow := 6;
  end
  else if vNum < 81 then
  begin
    vCol := vNum - 71;
    vRow := 7;
  end
  else if vNum < 91 then
  begin
    vCol := vNum - 81;
    vRow := 8;
  end
  else if vNum < 101 then
  begin
    vCol := vNum - 91;
    vRow := 9;
  end;
  if Assigned(imgHTTP2) then
  begin
    imgHTTP2.Canvas.Draw(vCol * 50, vRow * 50, oJPEG);
    FreeAndNil(oJPEG);
  end;
end;

procedure THTTP1_Thread.Execute;
var
  i: Integer;
  oStream: TMemoryStream;
  oJPEG: TJPEGImage;
  vCol, vRow: Integer;
  oHTTP: TsgcHTTP1Client;
begin
  inherited;

  FRMHTTP2_Client.imgHTTP.Picture.Graphic := nil;
  oHTTP := TsgcHTTP1Client.Create(nil);
  Try
    for i := 1 to 100 do
    begin
      oStream := TMemoryStream.Create;
      Try
        oHTTP.TLSOptions.Version := tls1_2;
        oHTTP.Get(URL + '/demo/img/http_test/h_' + Format('%.2d', [i]) + '.jpg', oStream);
        oJPEG := TJPEGImage.Create;
        oJPEG.Scale := jsHalf;
        oStream.Position := 0;
        oJPEG.LoadFromStream(oStream);
        if i < 11 then
        begin
          vCol := i - 1;
          vRow := 0;
        end
        else if i < 21 then
        begin
          vCol := i - 11;
          vRow := 1;
        end
        else if i < 31 then
        begin
          vCol := i - 21;
          vRow := 2;
        end
        else if i < 41 then
        begin
          vCol := i - 31;
          vRow := 3;
        end
        else if i < 51 then
        begin
          vCol := i - 41;
          vRow := 4;
        end
        else if i < 61 then
        begin
          vCol := i - 51;
          vRow := 5;
        end
        else if i < 71 then
        begin
          vCol := i - 61;
          vRow := 6;
        end
        else if i < 81 then
        begin
          vCol := i - 71;
          vRow := 7;
        end
        else if i < 91 then
        begin
          vCol := i - 81;
          vRow := 8;
        end
        else if i < 101 then
        begin
          vCol := i - 91;
          vRow := 9;
        end;
        TThread.Queue(nil,
        procedure
        begin
          FRMHTTP2_Client.imgHTTP.Canvas.Draw(vCol * 50, vRow * 50, oJPEG);
          FreeAndNil(oJPEG);
        end);
      Finally
        oStream.Free;
      End;
    end;
  Finally
    oHTTP.Free;
    Terminate;
  end;
end;

end.
```

