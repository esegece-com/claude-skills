# TsgcWebView2 - Example

Full source of `uWebView2Browser.pas` from the **50.Other/06.WebView2_Browser** demo, which uses `TsgcWebView2`.

API reference: [TsgcWebView2](../reference/api/TsgcWebView2.md)
Source demo: `50.Other/06.WebView2_Browser` (file `uWebView2Browser.pas`)

```pascal
{ ***************************************************************************
  sgcWebSocket component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit uWebView2Browser;

interface

uses
  Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs,
  StdCtrls, ExtCtrls,
  // sgc
  sgcWebView2_API, sgcWebView2_Classes, sgcWebView2;

type
  TfrmWebView2Browser = class(TForm)
    pnlToolbar: TPanel;
    lblJavaScript: TLabel;
    btnBack: TButton;
    btnForward: TButton;
    btnReload: TButton;
    btnStop: TButton;
    edtURL: TEdit;
    btnNavigate: TButton;
    edtJavaScript: TEdit;
    btnExecuteJS: TButton;
    btnDevTools: TButton;
    pnlStatus: TPanel;
    lblStatus: TLabel;
    pnlLog: TPanel;
    pnlLogHeader: TPanel;
    btnClearLog: TButton;
    chkLogEvents: TCheckBox;
    memoLog: TMemo;
    Splitter1: TSplitter;
    sgcWebView2: TsgcWebView2;
    btnCookies: TButton;
    btnPrint: TButton;
    btnPrintPdf: TButton;
    btnMute: TButton;
    btnClearData: TButton;
    btnTaskMgr: TButton;
    btnVHost: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnBackClick(Sender: TObject);
    procedure btnForwardClick(Sender: TObject);
    procedure btnReloadClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnNavigateClick(Sender: TObject);
    procedure btnExecuteJSClick(Sender: TObject);
    procedure btnDevToolsClick(Sender: TObject);
    procedure btnClearLogClick(Sender: TObject);
    procedure btnCookiesClick(Sender: TObject);
    procedure btnPrintClick(Sender: TObject);
    procedure btnPrintPdfClick(Sender: TObject);
    procedure btnMuteClick(Sender: TObject);
    procedure btnClearDataClick(Sender: TObject);
    procedure btnTaskMgrClick(Sender: TObject);
    procedure btnVHostClick(Sender: TObject);
    procedure sgcWebView2NavigationStarting(Sender: TObject; const aURI: string;
      aIsUserInitiated, aIsRedirected: Boolean; var aCancel: Boolean);
    procedure sgcWebView2NavigationCompleted(Sender: TObject;
      aIsSuccess: Boolean; aWebErrorStatus: Integer);
    procedure sgcWebView2SourceChanged(Sender: TObject;
      aIsNewDocument: Boolean);
    procedure sgcWebView2WebMessageReceived(Sender: TObject;
      const aSource, aWebMessageAsJson, aWebMessageAsString: string);
    procedure sgcWebView2NewWindowRequested(Sender: TObject; const aURI: string;
      aIsUserInitiated: Boolean; var aHandled: Boolean);
    procedure sgcWebView2DocumentTitleChanged(Sender: TObject;
      const aTitle: string);
    procedure sgcWebView2ScriptExecuted(Sender: TObject; aErrorCode: HRESULT;
      const aResultAsJson: string);
    procedure sgcWebView2ContentLoading(Sender: TObject; aIsErrorPage: Boolean);
    procedure sgcWebView2HistoryChanged(Sender: TObject);
    procedure sgcWebView2ProcessFailed(Sender: TObject; aKind: Integer);
    procedure sgcWebView2Initialized(Sender: TObject);
    procedure sgcWebView2DownloadStarting(Sender: TObject;
      const aURI, aResultFilePath: string; var aCancel: Boolean;
      var aHandled: Boolean; var aFilePath: string);
    procedure sgcWebView2DownloadCompleted(Sender: TObject;
      const aFilePath: string; aState: Integer);
    procedure sgcWebView2ContextMenuRequested(Sender: TObject;
      const aMenuItems: string; aContextKind: Integer; const aLocation: TPoint;
      var aHandled: Boolean);
    procedure sgcWebView2FaviconChanged(Sender: TObject;
      const aFaviconURI: string);
    procedure sgcWebView2ClientCertificateRequested(Sender: TObject;
      const aHost: string; aPort: Integer; var aHandled: Boolean);
    procedure sgcWebView2ServerCertificateError(Sender: TObject;
      const aRequestURI: string; aErrorStatus: Integer; var aAction: Integer);
    procedure sgcWebView2StatusBarTextChanged(Sender: TObject;
      const aText: string);
    procedure sgcWebView2DOMContentLoaded(Sender: TObject);
    procedure sgcWebView2BasicAuthRequested(Sender: TObject; const aURI: string;
      var aUserName, aPassword: string; var aHandled: Boolean);
  private
    procedure Log(const aText: string);
    procedure UpdateStatusBar;
  public
    { Public declarations }
  end;

var
  frmWebView2Browser: TfrmWebView2Browser;

implementation

{$R *.dfm}

procedure TfrmWebView2Browser.Log(const aText: string);
begin
  if chkLogEvents.Checked then
    memoLog.Lines.Add(FormatDateTime('hh:nn:ss.zzz', Now) + ' ' + aText);
end;

procedure TfrmWebView2Browser.UpdateStatusBar;
var
  vStatus: string;
begin
  vStatus := 'Profile: ' + sgcWebView2.GetProfileName;
  vStatus := vStatus + ' | Favicon: ' + sgcWebView2.FaviconURI;
  if sgcWebView2.IsDocumentPlayingAudio then
    vStatus := vStatus + ' | Audio: Yes'
  else
    vStatus := vStatus + ' | Audio: No';
  if sgcWebView2.IsMuted then
    vStatus := vStatus + ' | Muted: Yes'
  else
    vStatus := vStatus + ' | Muted: No';
  lblStatus.Caption := vStatus;
end;

procedure TfrmWebView2Browser.FormCreate(Sender: TObject);
begin
  memoLog.Lines.Clear;
  Log('Application started. Initializing WebView2...');
end;

{ --- Navigation buttons --- }

procedure TfrmWebView2Browser.btnBackClick(Sender: TObject);
begin
  sgcWebView2.GoBack;
end;

procedure TfrmWebView2Browser.btnForwardClick(Sender: TObject);
begin
  sgcWebView2.GoForward;
end;

procedure TfrmWebView2Browser.btnReloadClick(Sender: TObject);
begin
  sgcWebView2.Reload;
end;

procedure TfrmWebView2Browser.btnStopClick(Sender: TObject);
begin
  sgcWebView2.Stop;
end;

procedure TfrmWebView2Browser.btnNavigateClick(Sender: TObject);
begin
  if edtURL.Text <> '' then
    sgcWebView2.Navigate(edtURL.Text);
end;

{ --- JavaScript --- }

procedure TfrmWebView2Browser.btnExecuteJSClick(Sender: TObject);
begin
  if edtJavaScript.Text <> '' then
  begin
    Log('ExecuteScript: ' + edtJavaScript.Text);
    sgcWebView2.ExecuteScript(edtJavaScript.Text);
  end;
end;

procedure TfrmWebView2Browser.btnDevToolsClick(Sender: TObject);
begin
  sgcWebView2.OpenDevToolsWindow;
end;

{ --- Feature buttons --- }

procedure TfrmWebView2Browser.btnCookiesClick(Sender: TObject);
begin
  if sgcWebView2.CookieManager <> nil then
  begin
    Log('Requesting cookies for: ' + sgcWebView2.URL);
    sgcWebView2.CookieManager.GetCookies(sgcWebView2.URL);
  end
  else
    Log('CookieManager not available');
end;

procedure TfrmWebView2Browser.btnPrintClick(Sender: TObject);
begin
  sgcWebView2.ShowPrintUI;
  Log('ShowPrintUI called');
end;

procedure TfrmWebView2Browser.btnPrintPdfClick(Sender: TObject);
var
  vPath: string;
begin
  vPath := ExtractFilePath(Application.ExeName) + 'output.pdf';
  sgcWebView2.PrintToPdf(vPath);
  Log('PrintToPdf: ' + vPath);
end;

procedure TfrmWebView2Browser.btnMuteClick(Sender: TObject);
begin
  sgcWebView2.IsMuted := not sgcWebView2.IsMuted;
  if sgcWebView2.IsMuted then
    btnMute.Caption := 'Unmute'
  else
    btnMute.Caption := 'Mute';
  UpdateStatusBar;
  Log('Muted: ' +
{$IFDEF VER150}SysUtils.BoolToStr(sgcWebView2.IsMuted){$ELSE}BoolToStr
    (sgcWebView2.IsMuted, True){$ENDIF});
end;

procedure TfrmWebView2Browser.btnClearDataClick(Sender: TObject);
begin
  sgcWebView2.ClearAllBrowsingData;
  Log('ClearAllBrowsingData called');
end;

procedure TfrmWebView2Browser.btnTaskMgrClick(Sender: TObject);
begin
  sgcWebView2.OpenTaskManagerWindow;
  Log('OpenTaskManagerWindow called');
end;

procedure TfrmWebView2Browser.btnVHostClick(Sender: TObject);
var
  vHost, vFolder: string;
begin
  vHost := InputBox('Virtual Host', 'Host name (e.g. app.local):', 'app.local');
  if vHost <> '' then
  begin
    vFolder := InputBox('Virtual Host', 'Folder path:',
      ExtractFilePath(Application.ExeName));
    if vFolder <> '' then
    begin
      sgcWebView2.SetVirtualHostNameToFolderMapping(vHost, vFolder, 1);
      Log('VirtualHost: ' + vHost + ' -> ' + vFolder);
    end;
  end;
end;

{ --- Log --- }

procedure TfrmWebView2Browser.btnClearLogClick(Sender: TObject);
begin
  memoLog.Lines.Clear;
end;

{ --- WebView2 Events --- }

procedure TfrmWebView2Browser.sgcWebView2Initialized(Sender: TObject);
begin
  Log('WebView2 initialized successfully');
  UpdateStatusBar;
end;

procedure TfrmWebView2Browser.sgcWebView2NavigationStarting(Sender: TObject;
  const aURI: string; aIsUserInitiated, aIsRedirected: Boolean;
  var aCancel: Boolean);
begin
  Log('NavigationStarting: ' + aURI);
  edtURL.Text := aURI;
end;

procedure TfrmWebView2Browser.sgcWebView2NavigationCompleted(Sender: TObject;
  aIsSuccess: Boolean; aWebErrorStatus: Integer);
begin
  if aIsSuccess then
    Log('NavigationCompleted: Success')
  else
    Log('NavigationCompleted: Failed (error=' +
      IntToStr(aWebErrorStatus) + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2SourceChanged(Sender: TObject;
  aIsNewDocument: Boolean);
var
  vURL: string;
begin
  vURL := sgcWebView2.URL;
  if vURL <> '' then
    edtURL.Text := vURL;
  Log('SourceChanged: ' + vURL + ' (NewDocument=' +
{$IFDEF VER150}SysUtils.BoolToStr(aIsNewDocument){$ELSE}BoolToStr
    (aIsNewDocument, True){$ENDIF} + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2DocumentTitleChanged(Sender: TObject;
  const aTitle: string);
begin
  Caption := 'sgcWebView2 Browser Demo - ' + aTitle;
  Log('DocumentTitleChanged: ' + aTitle);
end;

procedure TfrmWebView2Browser.sgcWebView2WebMessageReceived(Sender: TObject;
  const aSource, aWebMessageAsJson, aWebMessageAsString: string);
begin
  Log('WebMessageReceived from ' + aSource + ': ' + aWebMessageAsString);
end;

procedure TfrmWebView2Browser.sgcWebView2NewWindowRequested(Sender: TObject;
  const aURI: string; aIsUserInitiated: Boolean; var aHandled: Boolean);
begin
  Log('NewWindowRequested: ' + aURI);
  { Navigate in same window instead of opening a new one }
  sgcWebView2.Navigate(aURI);
  aHandled := True;
end;

procedure TfrmWebView2Browser.sgcWebView2ScriptExecuted(Sender: TObject;
  aErrorCode: HRESULT; const aResultAsJson: string);
begin
  if aErrorCode = S_OK then
    Log('ScriptResult: ' + aResultAsJson)
  else
    Log('ScriptError: code=' + IntToStr(aErrorCode));
end;

procedure TfrmWebView2Browser.sgcWebView2ContentLoading(Sender: TObject;
  aIsErrorPage: Boolean);
begin
  Log('ContentLoading (ErrorPage=' +
{$IFDEF VER150}SysUtils.BoolToStr(aIsErrorPage){$ELSE}BoolToStr(aIsErrorPage,
    True){$ENDIF} + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2HistoryChanged(Sender: TObject);
begin
  Log('HistoryChanged (CanGoBack=' +
{$IFDEF VER150}SysUtils.BoolToStr(sgcWebView2.CanGoBack){$ELSE}BoolToStr
    (sgcWebView2.CanGoBack, True){$ENDIF} + ', CanGoForward=' +
{$IFDEF VER150}SysUtils.BoolToStr(sgcWebView2.CanGoForward){$ELSE}BoolToStr
    (sgcWebView2.CanGoForward, True){$ENDIF} + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2ProcessFailed(Sender: TObject;
  aKind: Integer);
begin
  Log('ProcessFailed: kind=' + IntToStr(aKind));
end;

procedure TfrmWebView2Browser.sgcWebView2DownloadStarting(Sender: TObject;
  const aURI, aResultFilePath: string; var aCancel: Boolean;
  var aHandled: Boolean; var aFilePath: string);
begin
  Log('DownloadStarting: ' + aURI + ' -> ' + aResultFilePath);
end;

procedure TfrmWebView2Browser.sgcWebView2DownloadCompleted(Sender: TObject;
  const aFilePath: string; aState: Integer);
begin
  Log('DownloadCompleted: ' + aFilePath + ' (state=' + IntToStr(aState) + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2ContextMenuRequested(Sender: TObject;
  const aMenuItems: string; aContextKind: Integer; const aLocation: TPoint;
  var aHandled: Boolean);
begin
  Log('ContextMenuRequested: kind=' + IntToStr(aContextKind) + ' at (' +
    IntToStr(aLocation.X) + ',' + IntToStr(aLocation.Y) + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2FaviconChanged(Sender: TObject;
  const aFaviconURI: string);
begin
  Log('FaviconChanged: ' + aFaviconURI);
  UpdateStatusBar;
end;

procedure TfrmWebView2Browser.sgcWebView2ClientCertificateRequested
  (Sender: TObject; const aHost: string; aPort: Integer; var aHandled: Boolean);
begin
  Log('ClientCertificateRequested: ' + aHost + ':' + IntToStr(aPort));
end;

procedure TfrmWebView2Browser.sgcWebView2ServerCertificateError(Sender: TObject;
  const aRequestURI: string; aErrorStatus: Integer; var aAction: Integer);
begin
  Log('ServerCertificateError: ' + aRequestURI + ' (status=' +
    IntToStr(aErrorStatus) + ')');
end;

procedure TfrmWebView2Browser.sgcWebView2StatusBarTextChanged(Sender: TObject;
  const aText: string);
begin
  Log('StatusBarText: ' + aText);
end;

procedure TfrmWebView2Browser.sgcWebView2DOMContentLoaded(Sender: TObject);
begin
  Log('DOMContentLoaded');
  UpdateStatusBar;
end;

procedure TfrmWebView2Browser.sgcWebView2BasicAuthRequested(Sender: TObject;
  const aURI: string; var aUserName, aPassword: string; var aHandled: Boolean);
begin
  Log('BasicAuthRequested: ' + aURI);
  aUserName := InputBox('Basic Auth - ' + aURI, 'Username:', '');
  if aUserName <> '' then
  begin
    aPassword := InputBox('Basic Auth - ' + aURI, 'Password:', '');
    aHandled := True;
    Log('BasicAuth: provided credentials for ' + aUserName);
  end;
end;

end.
```

