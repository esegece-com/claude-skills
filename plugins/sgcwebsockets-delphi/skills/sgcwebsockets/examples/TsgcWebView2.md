# TsgcWebView2 - Example

Usage of `TsgcWebView2` extracted from the **50.Other/06.WebView2_Browser** demo. See the full project for context.

API reference: [TsgcWebView2](../reference/api/TsgcWebView2.md)
Source demo: `50.Other/06.WebView2_Browser` (file `uWebView2Browser.pas`)

```pascal
vStatus := 'Profile: ' + sgcWebView2.GetProfileName;
vStatus := vStatus + ' | Favicon: ' + sgcWebView2.FaviconURI;
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
```

