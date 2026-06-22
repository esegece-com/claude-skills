# TsgcWebView2

unit: sgcWebView2
Edition: Standard

Add `sgcWebView2` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `URL: string (read-only)` | `string` | `__property UnicodeString URL /* read-only */;` |
| `DocumentTitle: string (read-only)` | `string` | `__property UnicodeString DocumentTitle /* read-only */;` |
| `CanGoBack: Boolean (read-only)` | `Boolean` | `__property bool CanGoBack /* read-only */;` |
| `CanGoForward: Boolean (read-only)` | `Boolean` | `__property bool CanGoForward /* read-only */;` |
| `Initialized: Boolean (read-only)` | `Boolean` | `__property bool Initialized /* read-only */;` |
| `WebView: ICoreWebView2 (read-only)` | [ICoreWebView2](../types/ICoreWebView2.md) | `__property ICoreWebView2 WebView /* read-only */;` |
| `Controller: ICoreWebView2Controller (read-only)` | [ICoreWebView2Controller](../types/ICoreWebView2Controller.md) | `__property ICoreWebView2Controller Controller /* read-only */;` |
| `Environment: ICoreWebView2Environment (read-only)` | [ICoreWebView2Environment](../types/ICoreWebView2Environment.md) | `__property ICoreWebView2Environment Environment /* read-only */;` |
| `CookieManager: TsgcWebView2CookieManager (read-only)` | [TsgcWebView2CookieManager](../types/TsgcWebView2CookieManager.md) | `__property TsgcWebView2CookieManager * CookieManager /* read-only */;` |
| `IsMuted: Boolean` | `Boolean` | `__property bool IsMuted;` |
| `IsDocumentPlayingAudio: Boolean (read-only)` | `Boolean` | `__property bool IsDocumentPlayingAudio /* read-only */;` |
| `FaviconURI: string (read-only)` | `string` | `__property UnicodeString FaviconURI /* read-only */;` |
| `StatusBarText: string (read-only)` | `string` | `__property UnicodeString StatusBarText /* read-only */;` |
| `DefaultURL: string` | `string` | `__property UnicodeString DefaultURL;` |
| `AutoInitialize: Boolean` | `Boolean` | `__property bool AutoInitialize;` |
| `ZoomFactor: Double` | `Double` | `__property double ZoomFactor;` |
| `UserDataFolder: string` | `string` | `__property UnicodeString UserDataFolder;` |
| `BrowserExecutableFolder: string` | `string` | `__property UnicodeString BrowserExecutableFolder;` |
| `Settings: TsgcWebView2Settings (read-only)` | [TsgcWebView2Settings](../types/TsgcWebView2Settings.md) | `__property TsgcWebView2Settings * Settings /* read-only */;` |
| `Align: TsgcHTMLChatMessageAlign` | [TsgcHTMLChatMessageAlign](../types/TsgcHTMLChatMessageAlign.md) | `__property TsgcHTMLChatMessageAlign * Align;` |
| `Anchors` |  | `__property Anchors;` |
| `Visible` |  | `__property Visible;` |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `TabOrder` |  | `__property TabOrder;` |
| `TabStop` |  | `__property TabStop;` |
| `PopupMenu` |  | `__property PopupMenu;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnNavigationStarting: TsgcWebView2NavigationStartingEvent` | [TsgcWebView2NavigationStartingEvent](../types/TsgcWebView2NavigationStartingEvent.md) | `__property TsgcWebView2NavigationStartingEvent OnNavigationStarting;` |
| `OnNavigationCompleted: TsgcWebView2NavigationCompletedEvent` | [TsgcWebView2NavigationCompletedEvent](../types/TsgcWebView2NavigationCompletedEvent.md) | `__property TsgcWebView2NavigationCompletedEvent OnNavigationCompleted;` |
| `OnSourceChanged: TsgcWebView2SourceChangedEvent` | [TsgcWebView2SourceChangedEvent](../types/TsgcWebView2SourceChangedEvent.md) | `__property TsgcWebView2SourceChangedEvent OnSourceChanged;` |
| `OnWebMessageReceived: TsgcWebView2WebMessageReceivedEvent` | [TsgcWebView2WebMessageReceivedEvent](../types/TsgcWebView2WebMessageReceivedEvent.md) | `__property TsgcWebView2WebMessageReceivedEvent OnWebMessageReceived;` |
| `OnNewWindowRequested: TsgcWebView2NewWindowRequestedEvent` | [TsgcWebView2NewWindowRequestedEvent](../types/TsgcWebView2NewWindowRequestedEvent.md) | `__property TsgcWebView2NewWindowRequestedEvent OnNewWindowRequested;` |
| `OnDocumentTitleChanged: TsgcWebView2DocumentTitleChangedEvent` | [TsgcWebView2DocumentTitleChangedEvent](../types/TsgcWebView2DocumentTitleChangedEvent.md) | `__property TsgcWebView2DocumentTitleChangedEvent OnDocumentTitleChanged;` |
| `OnScriptExecuted: TsgcWebView2ScriptExecutedEvent` | [TsgcWebView2ScriptExecutedEvent](../types/TsgcWebView2ScriptExecutedEvent.md) | `__property TsgcWebView2ScriptExecutedEvent OnScriptExecuted;` |
| `OnContentLoading: TsgcWebView2ContentLoadingEvent` | [TsgcWebView2ContentLoadingEvent](../types/TsgcWebView2ContentLoadingEvent.md) | `__property TsgcWebView2ContentLoadingEvent OnContentLoading;` |
| `OnHistoryChanged: TsgcWebView2HistoryChangedEvent` | [TsgcWebView2HistoryChangedEvent](../types/TsgcWebView2HistoryChangedEvent.md) | `__property TsgcWebView2HistoryChangedEvent OnHistoryChanged;` |
| `OnProcessFailed: TsgcWebView2ProcessFailedEvent` | [TsgcWebView2ProcessFailedEvent](../types/TsgcWebView2ProcessFailedEvent.md) | `__property TsgcWebView2ProcessFailedEvent OnProcessFailed;` |
| `OnPermissionRequested: TsgcWebView2PermissionRequestedEvent` | [TsgcWebView2PermissionRequestedEvent](../types/TsgcWebView2PermissionRequestedEvent.md) | `__property TsgcWebView2PermissionRequestedEvent OnPermissionRequested;` |
| `OnWindowCloseRequested: TsgcWebView2WindowCloseRequestedEvent` | [TsgcWebView2WindowCloseRequestedEvent](../types/TsgcWebView2WindowCloseRequestedEvent.md) | `__property TsgcWebView2WindowCloseRequestedEvent OnWindowCloseRequested;` |
| `OnInitialized: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnInitialized;` |
| `OnDownloadStarting: TsgcWebView2DownloadStartingEvent` | [TsgcWebView2DownloadStartingEvent](../types/TsgcWebView2DownloadStartingEvent.md) | `__property TsgcWebView2DownloadStartingEvent OnDownloadStarting;` |
| `OnDownloadProgress: TsgcWebView2DownloadProgressEvent` | [TsgcWebView2DownloadProgressEvent](../types/TsgcWebView2DownloadProgressEvent.md) | `__property TsgcWebView2DownloadProgressEvent OnDownloadProgress;` |
| `OnDownloadCompleted: TsgcWebView2DownloadCompletedEvent` | [TsgcWebView2DownloadCompletedEvent](../types/TsgcWebView2DownloadCompletedEvent.md) | `__property TsgcWebView2DownloadCompletedEvent OnDownloadCompleted;` |
| `OnContextMenuRequested: TsgcWebView2ContextMenuRequestedEvent` | [TsgcWebView2ContextMenuRequestedEvent](../types/TsgcWebView2ContextMenuRequestedEvent.md) | `__property TsgcWebView2ContextMenuRequestedEvent OnContextMenuRequested;` |
| `OnFaviconChanged: TsgcWebView2FaviconChangedEvent` | [TsgcWebView2FaviconChangedEvent](../types/TsgcWebView2FaviconChangedEvent.md) | `__property TsgcWebView2FaviconChangedEvent OnFaviconChanged;` |
| `OnClientCertificateRequested: TsgcWebView2ClientCertificateRequestedEvent` | [TsgcWebView2ClientCertificateRequestedEvent](../types/TsgcWebView2ClientCertificateRequestedEvent.md) | `__property TsgcWebView2ClientCertificateRequestedEvent OnClientCertificateRequested;` |
| `OnServerCertificateError: TsgcWebView2ServerCertificateErrorEvent` | [TsgcWebView2ServerCertificateErrorEvent](../types/TsgcWebView2ServerCertificateErrorEvent.md) | `__property TsgcWebView2ServerCertificateErrorEvent OnServerCertificateError;` |
| `OnStatusBarTextChanged: TsgcWebView2StatusBarTextChangedEvent` | [TsgcWebView2StatusBarTextChangedEvent](../types/TsgcWebView2StatusBarTextChangedEvent.md) | `__property TsgcWebView2StatusBarTextChangedEvent OnStatusBarTextChanged;` |
| `OnDOMContentLoaded: TsgcWebView2DOMContentLoadedEvent` | [TsgcWebView2DOMContentLoadedEvent](../types/TsgcWebView2DOMContentLoadedEvent.md) | `__property TsgcWebView2DOMContentLoadedEvent OnDOMContentLoaded;` |
| `OnBasicAuthRequested: TsgcWebView2BasicAuthRequestedEvent` | [TsgcWebView2BasicAuthRequestedEvent](../types/TsgcWebView2BasicAuthRequestedEvent.md) | `__property TsgcWebView2BasicAuthRequestedEvent OnBasicAuthRequested;` |
| `OnCapturePreviewCompleted: TsgcWebView2CapturePreviewCompletedEvent` | [TsgcWebView2CapturePreviewCompletedEvent](../types/TsgcWebView2CapturePreviewCompletedEvent.md) | `__property TsgcWebView2CapturePreviewCompletedEvent OnCapturePreviewCompleted;` |
| `OnInitScriptCompleted: TsgcWebView2InitScriptCompletedEvent` | [TsgcWebView2InitScriptCompletedEvent](../types/TsgcWebView2InitScriptCompletedEvent.md) | `__property TsgcWebView2InitScriptCompletedEvent OnInitScriptCompleted;` |
| `OnClick: string` | `string` | `__property UnicodeString OnClick;` |
| `OnDblClick` |  | `__property OnDblClick;` |
| `OnEnter` |  | `__property OnEnter;` |
| `OnExit` |  | `__property OnExit;` |
| `OnKeyDown` |  | `__property OnKeyDown;` |
| `OnKeyPress` |  | `__property OnKeyPress;` |
| `OnKeyUp` |  | `__property OnKeyUp;` |
| `OnMouseDown` |  | `__property OnMouseDown;` |
| `OnMouseMove` |  | `__property OnMouseMove;` |
| `OnMouseUp` |  | `__property OnMouseUp;` |

## Methods

Delphi

```pascal
procedure InitializeWebView;
procedure FinalizeWebView;
procedure Navigate(const aURL: string);
procedure NavigateToString(const aHTML: string);
procedure GoBack;
procedure GoForward;
procedure Reload;
procedure Stop;
procedure ExecuteScript(const aScript: string);
procedure PostWebMessageAsString(const aMessage: string);
procedure PostWebMessageAsJson(const aJson: string);
procedure OpenDevToolsWindow;
function GetProfileName: string;
procedure ClearBrowsingData(aKinds: Cardinal);
procedure ClearAllBrowsingData;
procedure PrintToPdf(const aFilePath: string);
procedure ShowPrintUI;
procedure SetVirtualHostNameToFolderMapping(const aHostName, aFolderPath: string; aAccessKind: Integer);
procedure ClearVirtualHostNameToFolderMapping(const aHostName: string);
procedure PostSharedBufferToScript(const aSharedBuffer: IUnknown; aAccess: Integer; const aAdditionalDataAsJson: string);
procedure OpenTaskManagerWindow;
procedure CapturePreview(aStream: TStream; aFormat: Integer);
procedure CapturePreviewToFile(const aFilePath: string; aFormat: Integer);
procedure AddInitScript(const aScript: string);
procedure RemoveInitScript(const aScriptId: string);
procedure RemoveAllInitScripts;
procedure NavigateWithPostData(const aURI, aMethod, aPostData, aHeaders: string);
function ExecuteScriptSync(const aScript: string): string;
```

C++Builder

```cpp
void __fastcall InitializeWebView();
void __fastcall FinalizeWebView();
void __fastcall Navigate(const UnicodeString aURL);
void __fastcall NavigateToString(const UnicodeString aHTML);
void __fastcall GoBack();
void __fastcall GoForward();
void __fastcall Reload();
void __fastcall Stop();
void __fastcall ExecuteScript(const UnicodeString aScript);
void __fastcall PostWebMessageAsString(const UnicodeString aMessage);
void __fastcall PostWebMessageAsJson(const UnicodeString aJson);
void __fastcall OpenDevToolsWindow();
UnicodeString __fastcall GetProfileName();
void __fastcall ClearBrowsingData(unsigned int aKinds);
void __fastcall ClearAllBrowsingData();
void __fastcall PrintToPdf(const UnicodeString aFilePath);
void __fastcall ShowPrintUI();
void __fastcall SetVirtualHostNameToFolderMapping(const UnicodeString aHostName, const UnicodeString aFolderPath, int aAccessKind);
void __fastcall ClearVirtualHostNameToFolderMapping(const UnicodeString aHostName);
void __fastcall PostSharedBufferToScript(const IUnknown aSharedBuffer, int aAccess, const UnicodeString aAdditionalDataAsJson);
void __fastcall OpenTaskManagerWindow();
void __fastcall CapturePreview(TStream * aStream, int aFormat);
void __fastcall CapturePreviewToFile(const UnicodeString aFilePath, int aFormat);
void __fastcall AddInitScript(const UnicodeString aScript);
void __fastcall RemoveInitScript(const UnicodeString aScriptId);
void __fastcall RemoveAllInitScripts();
void __fastcall NavigateWithPostData(const UnicodeString aURI, const UnicodeString aMethod, const UnicodeString aPostData, const UnicodeString aHeaders);
UnicodeString __fastcall ExecuteScriptSync(const UnicodeString aScript);
```

