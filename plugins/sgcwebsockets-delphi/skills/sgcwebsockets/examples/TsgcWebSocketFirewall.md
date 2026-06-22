# TsgcWebSocketFirewall - Example

Full source of `uFirewallDemo.pas` from the **04.WebSocket_Other_Samples/13.Firewall** demo, which uses `TsgcWebSocketFirewall`.

API reference: [TsgcWebSocketFirewall](../reference/api/TsgcWebSocketFirewall.md)
Source demo: `04.WebSocket_Other_Samples/13.Firewall` (file `uFirewallDemo.pas`)

```pascal
unit uFirewallDemo;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, ComCtrls,
  // sgc
  sgcWebSocket_Classes, sgcWebSocket_Types, sgcWebSocket,
  sgcBase_Classes, sgcTCP_Classes, sgcSocket_Classes,
  sgcWebSocket_Server_Firewall, sgcWebSocket_Server;

type
  TfrmFirewallDemo = class(TForm)
    pnlTop: TPanel;
    lblPort: TLabel;
    txtPort: TEdit;
    btnStart: TButton;
    btnStop: TButton;
    lblStatus: TLabel;
    pnlLeft: TPanel;
    PageControl1: TPageControl;
    tsIPFiltering: TTabSheet;
    gbBlacklist: TGroupBox;
    chkBlacklist: TCheckBox;
    memoBlacklist: TMemo;
    btnApplyBlacklist: TButton;
    gbWhitelist: TGroupBox;
    chkWhitelist: TCheckBox;
    memoWhitelist: TMemo;
    btnApplyWhitelist: TButton;
    gbManualBan: TGroupBox;
    lblBanIP: TLabel;
    txtBanIP: TEdit;
    btnBanIP: TButton;
    btnUnbanIP: TButton;
    btnClearBans: TButton;
    lblBanDurationManual: TLabel;
    txtBanDurationManual: TEdit;
    tsProtection: TTabSheet;
    gbBruteForce: TGroupBox;
    chkBruteForce: TCheckBox;
    lblMaxAttempts: TLabel;
    txtMaxAttempts: TEdit;
    lblBanDuration: TLabel;
    txtBanDuration: TEdit;
    btnApplyBruteForce: TButton;
    gbRateLimit: TGroupBox;
    chkRateLimit: TCheckBox;
    lblMaxConnIP: TLabel;
    txtMaxConnIP: TEdit;
    gbContentFilter: TGroupBox;
    chkSQLInjection: TCheckBox;
    chkXSS: TCheckBox;
    chkFloodProtection: TCheckBox;
    lblMaxMsgSec: TLabel;
    txtMaxMsgSec: TEdit;
    tsAdvanced: TTabSheet;
    gbPayloadLimit: TGroupBox;
    chkPayloadLimit: TCheckBox;
    txtMaxPayloadSize: TEdit;
    lblPayloadBytes: TLabel;
    gbPathTraversal: TGroupBox;
    chkPathTraversal: TCheckBox;
    gbCommandInjection: TGroupBox;
    chkCommandInjection: TCheckBox;
    tsGeoIP: TTabSheet;
    gbGeoIP: TGroupBox;
    chkGeoIP: TCheckBox;
    rbBlockList: TRadioButton;
    rbAllowList: TRadioButton;
    memoCountries: TMemo;
    btnLoadGeoIPDB: TButton;
    lblGeoIPStatus: TLabel;
    tsThreatIntel: TTabSheet;
    gbThreatScore: TGroupBox;
    chkThreatScore: TCheckBox;
    lblAutobanThreshold: TLabel;
    txtAutobanThreshold: TEdit;
    lblDecayPerHour: TLabel;
    txtDecayPerHour: TEdit;
    gbBanEscalation: TGroupBox;
    chkBanEscalation: TCheckBox;
    memoBanLevels: TMemo;
    lblEscalationReset: TLabel;
    txtEscalationReset: TEdit;
    tsWebSocket: TTabSheet;
    gbWSProtection: TGroupBox;
    chkWSProtection: TCheckBox;
    lblMaxFrameSize: TLabel;
    txtMaxFrameSize: TEdit;
    lblAllowedOrigins: TLabel;
    memoOrigins: TMemo;
    btnApplyOrigins: TButton;
    lblAllowedSubprotocols: TLabel;
    memoSubprotocols: TMemo;
    btnApplySubprotocols: TButton;
    tsCustomRules: TTabSheet;
    gbCustomRules: TGroupBox;
    chkRulesEnabled: TCheckBox;
    lbRules: TListBox;
    btnRemoveRule: TButton;
    lblRuleName: TLabel;
    txtRuleName: TEdit;
    lblRuleIPPattern: TLabel;
    txtRuleIPPattern: TEdit;
    lblRuleMinViolations: TLabel;
    txtRuleMinViolations: TEdit;
    lblRuleTimeWindow: TLabel;
    txtRuleTimeWindow: TEdit;
    lblRuleMessagePattern: TLabel;
    txtRuleMessagePattern: TEdit;
    lblRuleCountryCode: TLabel;
    txtRuleCountryCode: TEdit;
    lblRuleAction: TLabel;
    cmbRuleAction: TComboBox;
    lblRuleBanDuration: TLabel;
    txtRuleBanDuration: TEdit;
    btnAddRule: TButton;
    tsBotDetection: TTabSheet;
    gbBotMain: TGroupBox;
    lblKnownBotsFile: TLabel;
    lblCacheDuration: TLabel;
    lblDNSTimeout: TLabel;
    chkBotDetection: TCheckBox;
    txtKnownBotsFile: TEdit;
    btnLoadKnownBots: TButton;
    txtCacheDuration: TEdit;
    txtDNSTimeout: TEdit;
    btnApplyBotDetection: TButton;
    gbBotReverseDNS: TGroupBox;
    chkReverseDNS: TCheckBox;
    gbBotDatacenter: TGroupBox;
    lblASNFile: TLabel;
    chkDatacenter: TCheckBox;
    txtASNFile: TEdit;
    btnLoadASN: TButton;
    gbBotDNSBL: TGroupBox;
    lblDNSBLZones: TLabel;
    chkDNSBL: TCheckBox;
    memoDNSBLZones: TMemo;
    btnApplyDNSBL: TButton;
    gbBotTest: TGroupBox;
    lblTestIP: TLabel;
    lblBotResult: TLabel;
    txtTestIP: TEdit;
    btnClassifyIP: TButton;
    pnlRight: TPanel;
    memoLog: TMemo;
    pnlStats: TPanel;
    gbRealTimeStats: TGroupBox;
    lblStatConnections: TLabel;
    lblStatTotalConn: TLabel;
    lblStatBlocked: TLabel;
    lblStatMessages: TLabel;
    lblStatViolations: TLabel;
    lblStatSQLi: TLabel;
    lblStatXSS: TLabel;
    lblStatFlood: TLabel;
    lblStatGeoIP: TLabel;
    lblStatPathTraversal: TLabel;
    lblStatCmdInj: TLabel;
    lblStatPayload: TLabel;
    lblStatThreatScore: TLabel;
    lblStatCustomRule: TLabel;
    lblStatBot: TLabel;
    WSServer: TsgcWebSocketHTTPServer;
    Firewall: TsgcWebSocketFirewall;
    tmrStats: TTimer;
    OpenDialog1: TOpenDialog;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerException(Connection: TsgcWSConnection; E: Exception);
    procedure FirewallFiltered(Sender: TObject; const aIP: string;
      const aReason: string; var Allow: Boolean);
    procedure FirewallViolation(Sender: TObject; const aIP: string;
      const aViolationType: TsgcFirewallViolationType; const aDetails: string);
    procedure FirewallThreatScoreChanged(Sender: TObject; const aIP: string;
      aOldScore, aNewScore: Integer);
    procedure chkBlacklistClick(Sender: TObject);
    procedure chkWhitelistClick(Sender: TObject);
    procedure chkBruteForceClick(Sender: TObject);
    procedure chkSQLInjectionClick(Sender: TObject);
    procedure chkXSSClick(Sender: TObject);
    procedure chkFloodProtectionClick(Sender: TObject);
    procedure chkRateLimitClick(Sender: TObject);
    procedure btnApplyBlacklistClick(Sender: TObject);
    procedure btnApplyWhitelistClick(Sender: TObject);
    procedure btnApplyBruteForceClick(Sender: TObject);
    procedure btnBanIPClick(Sender: TObject);
    procedure btnUnbanIPClick(Sender: TObject);
    procedure btnClearBansClick(Sender: TObject);
    procedure chkPayloadLimitClick(Sender: TObject);
    procedure chkPathTraversalClick(Sender: TObject);
    procedure chkCommandInjectionClick(Sender: TObject);
    procedure chkGeoIPClick(Sender: TObject);
    procedure rbBlockListClick(Sender: TObject);
    procedure rbAllowListClick(Sender: TObject);
    procedure btnLoadGeoIPDBClick(Sender: TObject);
    procedure chkThreatScoreClick(Sender: TObject);
    procedure chkBanEscalationClick(Sender: TObject);
    procedure chkWSProtectionClick(Sender: TObject);
    procedure btnApplyOriginsClick(Sender: TObject);
    procedure btnApplySubprotocolsClick(Sender: TObject);
    procedure chkRulesEnabledClick(Sender: TObject);
    procedure btnAddRuleClick(Sender: TObject);
    procedure btnRemoveRuleClick(Sender: TObject);
    procedure tmrStatsTimer(Sender: TObject);
    procedure chkBotDetectionClick(Sender: TObject);
    procedure btnApplyBotDetectionClick(Sender: TObject);
    procedure btnLoadKnownBotsClick(Sender: TObject);
    procedure chkReverseDNSClick(Sender: TObject);
    procedure chkDatacenterClick(Sender: TObject);
    procedure btnLoadASNClick(Sender: TObject);
    procedure chkDNSBLClick(Sender: TObject);
    procedure btnApplyDNSBLClick(Sender: TObject);
    procedure btnClassifyIPClick(Sender: TObject);
    procedure FirewallBotDetected(Sender: TObject; const aIP: string;
      aClassification: TsgcBotClassification; const aBotName: string);
  private
    FBlockedCount: Integer;
    FConnectionCount: Integer;
    procedure DoLog(const aText: string);
    function ViolationTypeToStr(aType: TsgcFirewallViolationType): string;
    function BotClassificationToStr(aClass: TsgcBotClassification): string;
  end;

var
  frmFirewallDemo: TfrmFirewallDemo;

implementation

uses
  StrUtils;

{$R *.dfm}

procedure TfrmFirewallDemo.FormCreate(Sender: TObject);
begin
  FBlockedCount := 0;
  FConnectionCount := 0;
  WSServer.Firewall := Firewall;
  Firewall.OnThreatScoreChanged := FirewallThreatScoreChanged;
  Firewall.OnBotDetected := FirewallBotDetected;
  PageControl1.ActivePageIndex := 0;
  cmbRuleAction.ItemIndex := 0;
  DoLog('Firewall demo ready. Configure settings and click Start.');
  DoLog('The firewall is automatically integrated with the server.');
end;

procedure TfrmFirewallDemo.DoLog(const aText: string);
begin
  if memoLog.Lines.Count > 5000 then
    memoLog.Lines.Clear;
  memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aText);
end;

function TfrmFirewallDemo.ViolationTypeToStr
  (aType: TsgcFirewallViolationType): string;
begin
  case aType of
    fvBlacklist:
      Result := 'BLACKLIST';
    fvWhitelist:
      Result := 'WHITELIST';
    fvBruteForce:
      Result := 'BRUTE_FORCE';
    fvRateLimit:
      Result := 'RATE_LIMIT';
    fvFlood:
      Result := 'FLOOD';
    fvSQLInjection:
      Result := 'SQL_INJECTION';
    fvXSS:
      Result := 'XSS';
    fvGeoIP:
      Result := 'GEO_IP';
    fvPathTraversal:
      Result := 'PATH_TRAVERSAL';
    fvCommandInjection:
      Result := 'COMMAND_INJECTION';
    fvPayloadSize:
      Result := 'PAYLOAD_SIZE';
    fvOrigin:
      Result := 'ORIGIN';
    fvFrameSize:
      Result := 'FRAME_SIZE';
    fvThreatScore:
      Result := 'THREAT_SCORE';
    fvCustomRule:
      Result := 'CUSTOM_RULE';
    fvBot:
      Result := 'BOT';
  else
    Result := 'UNKNOWN';
  end;
end;

function TfrmFirewallDemo.BotClassificationToStr
  (aClass: TsgcBotClassification): string;
begin
  case aClass of
    bcVerifiedCrawler:
      Result := 'VERIFIED CRAWLER';
    bcDatacenter:
      Result := 'DATACENTER';
    bcSuspectedBot:
      Result := 'SUSPECTED BOT';
    bcBlocklisted:
      Result := 'BLOCKLISTED';
    bcHuman:
      Result := 'HUMAN';
  else
    Result := 'UNKNOWN';
  end;
end;

// --- Server events ---

procedure TfrmFirewallDemo.btnStartClick(Sender: TObject);
begin
  WSServer.Port := StrToIntDef(txtPort.Text, 80);
  WSServer.Active := True;
  lblStatus.Caption := 'Running';
  lblStatus.Font.Color := clGreen;
  DoLog('Server started on port ' + IntToStr(WSServer.Port));
end;

procedure TfrmFirewallDemo.btnStopClick(Sender: TObject);
begin
  WSServer.Active := False;
  lblStatus.Caption := 'Stopped';
  lblStatus.Font.Color := clRed;
  FConnectionCount := 0;
  DoLog('Server stopped');
end;

procedure TfrmFirewallDemo.WSServerConnect(Connection: TsgcWSConnection);
begin
  Inc(FConnectionCount);
  DoLog('[CONNECT] ' + Connection.IP);
end;

procedure TfrmFirewallDemo.WSServerDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  Dec(FConnectionCount);
  if FConnectionCount < 0 then
    FConnectionCount := 0;
  DoLog('[DISCONNECT] ' + Connection.IP + ' (Code: ' + IntToStr(Code) + ')');
end;

procedure TfrmFirewallDemo.WSServerMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog('[MESSAGE] ' + Connection.IP + ': ' + Text);
end;

procedure TfrmFirewallDemo.WSServerError(Connection: TsgcWSConnection;
  const Error: string);
begin
  DoLog('[ERROR] ' + Error);
end;

procedure TfrmFirewallDemo.WSServerException(Connection: TsgcWSConnection;
  E: Exception);
begin
  DoLog('[EXCEPTION] ' + E.Message);
end;

// --- Firewall events ---

procedure TfrmFirewallDemo.FirewallFiltered(Sender: TObject; const aIP: string;
  const aReason: string; var Allow: Boolean);
begin
  if not Allow then
  begin
    Inc(FBlockedCount);
    DoLog('[BLOCKED] ' + aIP + ' - ' + aReason);
  end;
end;

procedure TfrmFirewallDemo.FirewallViolation(Sender: TObject; const aIP: string;
  const aViolationType: TsgcFirewallViolationType; const aDetails: string);
begin
  DoLog('[VIOLATION] ' + ViolationTypeToStr(aViolationType) + ' from ' + aIP +
    ': ' + aDetails);
end;

procedure TfrmFirewallDemo.FirewallThreatScoreChanged(Sender: TObject;
  const aIP: string; aOldScore, aNewScore: Integer);
begin
  DoLog('[THREAT] ' + aIP + ': score ' + IntToStr(aOldScore) + ' -> ' +
    IntToStr(aNewScore));
end;

// --- Blacklist ---

procedure TfrmFirewallDemo.chkBlacklistClick(Sender: TObject);
begin
  Firewall.Blacklist.Enabled := chkBlacklist.Checked;
  DoLog('Blacklist ' + IfThen(chkBlacklist.Checked, 'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyBlacklistClick(Sender: TObject);
begin
  Firewall.Blacklist.IPs.Assign(memoBlacklist.Lines);
  Firewall.Blacklist.Enabled := chkBlacklist.Checked;
  DoLog('Blacklist updated: ' + IntToStr(memoBlacklist.Lines.Count) +
    ' entries');
end;

// --- Whitelist ---

procedure TfrmFirewallDemo.chkWhitelistClick(Sender: TObject);
begin
  Firewall.Whitelist.Enabled := chkWhitelist.Checked;
  DoLog('Whitelist ' + IfThen(chkWhitelist.Checked, 'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyWhitelistClick(Sender: TObject);
begin
  Firewall.Whitelist.IPs.Assign(memoWhitelist.Lines);
  Firewall.Whitelist.Enabled := chkWhitelist.Checked;
  DoLog('Whitelist updated: ' + IntToStr(memoWhitelist.Lines.Count) +
    ' entries');
end;

// --- Brute Force ---

procedure TfrmFirewallDemo.chkBruteForceClick(Sender: TObject);
begin
  Firewall.BruteForce.Enabled := chkBruteForce.Checked;
  DoLog('Brute Force protection ' + IfThen(chkBruteForce.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyBruteForceClick(Sender: TObject);
begin
  Firewall.BruteForce.MaxAttempts := StrToIntDef(txtMaxAttempts.Text, 5);
  Firewall.BruteForce.BanDurationSec := StrToIntDef(txtBanDuration.Text, 300);
  Firewall.BruteForce.Enabled := chkBruteForce.Checked;
  DoLog('Brute Force settings: MaxAttempts=' +
    IntToStr(Firewall.BruteForce.MaxAttempts) + ', BanDuration=' +
    IntToStr(Firewall.BruteForce.BanDurationSec) + 's');
end;

// --- Content Filters ---

procedure TfrmFirewallDemo.chkSQLInjectionClick(Sender: TObject);
begin
  Firewall.SQLInjection.Enabled := chkSQLInjection.Checked;
  DoLog('SQL Injection detection ' + IfThen(chkSQLInjection.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.chkXSSClick(Sender: TObject);
begin
  Firewall.XSS.Enabled := chkXSS.Checked;
  DoLog('XSS detection ' + IfThen(chkXSS.Checked, 'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.chkFloodProtectionClick(Sender: TObject);
begin
  Firewall.FloodProtection.Enabled := chkFloodProtection.Checked;
  Firewall.FloodProtection.MaxMessagesPerSec :=
    StrToIntDef(txtMaxMsgSec.Text, 100);
  DoLog('Flood Protection ' + IfThen(chkFloodProtection.Checked, 'enabled',
    'disabled'));
end;

// --- Rate Limit ---

procedure TfrmFirewallDemo.chkRateLimitClick(Sender: TObject);
begin
  Firewall.RateLimit.Enabled := chkRateLimit.Checked;
  Firewall.RateLimit.MaxConnectionsPerIP := StrToIntDef(txtMaxConnIP.Text, 10);
  DoLog('Rate Limiting ' + IfThen(chkRateLimit.Checked, 'enabled', 'disabled') +
    ' (Max ' + IntToStr(Firewall.RateLimit.MaxConnectionsPerIP) + ' conn/IP)');
end;

// --- Manual Ban ---

procedure TfrmFirewallDemo.btnBanIPClick(Sender: TObject);
var
  vDuration: Integer;
begin
  if txtBanIP.Text <> '' then
  begin
    vDuration := StrToIntDef(txtBanDurationManual.Text, 0);
    Firewall.BanIP(txtBanIP.Text, vDuration);
    if vDuration = 0 then
      DoLog('Banned IP: ' + txtBanIP.Text + ' (permanent)')
    else
      DoLog('Banned IP: ' + txtBanIP.Text + ' (' + IntToStr(vDuration) + 's)');
  end;
end;

procedure TfrmFirewallDemo.btnUnbanIPClick(Sender: TObject);
begin
  if txtBanIP.Text <> '' then
  begin
    Firewall.UnbanIP(txtBanIP.Text);
    DoLog('Unbanned IP: ' + txtBanIP.Text);
  end;
end;

procedure TfrmFirewallDemo.btnClearBansClick(Sender: TObject);
begin
  Firewall.ClearBans;
  DoLog('All bans cleared');
end;

// --- Advanced Protection ---

procedure TfrmFirewallDemo.chkPayloadLimitClick(Sender: TObject);
begin
  Firewall.PayloadLimit.Enabled := chkPayloadLimit.Checked;
  Firewall.PayloadLimit.MaxSizeBytes :=
    StrToIntDef(txtMaxPayloadSize.Text, 1048576);
  DoLog('Payload Limit ' + IfThen(chkPayloadLimit.Checked, 'enabled',
    'disabled') + ' (Max ' + txtMaxPayloadSize.Text + ' bytes)');
end;

procedure TfrmFirewallDemo.chkPathTraversalClick(Sender: TObject);
begin
  Firewall.PathTraversal.Enabled := chkPathTraversal.Checked;
  DoLog('Path Traversal detection ' + IfThen(chkPathTraversal.Checked,
    'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.chkCommandInjectionClick(Sender: TObject);
begin
  Firewall.CommandInjection.Enabled := chkCommandInjection.Checked;
  DoLog('Command Injection detection ' + IfThen(chkCommandInjection.Checked,
    'enabled', 'disabled'));
end;

// --- GeoIP ---

procedure TfrmFirewallDemo.chkGeoIPClick(Sender: TObject);
begin
  Firewall.GeoIP.Enabled := chkGeoIP.Checked;
  if rbAllowList.Checked then
    Firewall.GeoIP.Mode := gmAllowList
  else
    Firewall.GeoIP.Mode := gmBlockList;
  Firewall.GeoIP.Countries.Assign(memoCountries.Lines);
  DoLog('GeoIP ' + IfThen(chkGeoIP.Checked, 'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.rbBlockListClick(Sender: TObject);
begin
  if chkGeoIP.Checked then
  begin
    Firewall.GeoIP.Mode := gmBlockList;
    DoLog('GeoIP mode: Block List');
  end;
end;

procedure TfrmFirewallDemo.rbAllowListClick(Sender: TObject);
begin
  if chkGeoIP.Checked then
  begin
    Firewall.GeoIP.Mode := gmAllowList;
    DoLog('GeoIP mode: Allow List');
  end;
end;

procedure TfrmFirewallDemo.btnLoadGeoIPDBClick(Sender: TObject);
var
  vDir, vLocationsFile: string;
begin
  OpenDialog1.Filter := 'CSV files (*.csv)|*.csv|All files (*.*)|*.*';
  if OpenDialog1.Execute then
  begin
    vDir := ExtractFilePath(OpenDialog1.FileName);
    vLocationsFile := vDir + 'GeoLite2-Country-Locations-en.csv';

    if FileExists(vLocationsFile) and (Pos('Blocks', OpenDialog1.FileName) > 0)
    then
    begin
      Firewall.GeoIP.BlocksFile := OpenDialog1.FileName;
      Firewall.GeoIP.LocationsFile := vLocationsFile;
      Firewall.LoadGeoIPDatabase(OpenDialog1.FileName);
      lblGeoIPStatus.Caption := 'GeoLite2 loaded';
      DoLog('GeoIP BlocksFile: ' + ExtractFileName(OpenDialog1.FileName));
      DoLog('GeoIP LocationsFile: ' + ExtractFileName(vLocationsFile));
    end
    else
    begin
      Firewall.LoadGeoIPDatabase(OpenDialog1.FileName);
      lblGeoIPStatus.Caption := 'Database loaded';
      DoLog('GeoIP database: ' + ExtractFileName(OpenDialog1.FileName));
    end;
  end;
end;

// --- Threat Intelligence ---

procedure TfrmFirewallDemo.chkThreatScoreClick(Sender: TObject);
begin
  Firewall.ThreatScore.Enabled := chkThreatScore.Checked;
  Firewall.ThreatScore.AutoBanThreshold :=
    StrToIntDef(txtAutobanThreshold.Text, 80);
  Firewall.ThreatScore.DecayPerHour := StrToIntDef(txtDecayPerHour.Text, 5);
  DoLog('Threat Score ' + IfThen(chkThreatScore.Checked, 'enabled', 'disabled')
    + ' (Threshold: ' + txtAutobanThreshold.Text + ')');
end;

procedure TfrmFirewallDemo.chkBanEscalationClick(Sender: TObject);
begin
  Firewall.BanEscalation.Enabled := chkBanEscalation.Checked;
  Firewall.BanEscalation.Levels.Assign(memoBanLevels.Lines);
  Firewall.BanEscalation.ResetAfterSec :=
    StrToIntDef(txtEscalationReset.Text, 86400);
  DoLog('Ban Escalation ' + IfThen(chkBanEscalation.Checked, 'enabled',
    'disabled'));
end;

// --- WebSocket Protection ---

procedure TfrmFirewallDemo.chkWSProtectionClick(Sender: TObject);
begin
  Firewall.WebSocketProtection.Enabled := chkWSProtection.Checked;
  Firewall.WebSocketProtection.MaxFrameSize :=
    StrToIntDef(txtMaxFrameSize.Text, 0);
  DoLog('WebSocket Protection ' + IfThen(chkWSProtection.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyOriginsClick(Sender: TObject);
begin
  Firewall.WebSocketProtection.AllowedOrigins.Assign(memoOrigins.Lines);
  DoLog('Allowed Origins updated: ' + IntToStr(memoOrigins.Lines.Count) +
    ' entries');
end;

procedure TfrmFirewallDemo.btnApplySubprotocolsClick(Sender: TObject);
begin
  Firewall.WebSocketProtection.AllowedSubprotocols.Assign
    (memoSubprotocols.Lines);
  DoLog('Allowed Subprotocols updated: ' +
    IntToStr(memoSubprotocols.Lines.Count) + ' entries');
end;

// --- Custom Rules ---

procedure TfrmFirewallDemo.chkRulesEnabledClick(Sender: TObject);
begin
  Firewall.CustomRules.Enabled := chkRulesEnabled.Checked;
  DoLog('Custom Rules ' + IfThen(chkRulesEnabled.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.btnAddRuleClick(Sender: TObject);
var
  vRule: TsgcFirewallRuleItem;
begin
  vRule := TsgcFirewallRuleItem(Firewall.CustomRules.Rules.Add);
  vRule.Name := txtRuleName.Text;
  vRule.Enabled := True;
  vRule.IPPattern := txtRuleIPPattern.Text;
  vRule.MinViolations := StrToIntDef(txtRuleMinViolations.Text, 0);
  vRule.TimeWindowSec := StrToIntDef(txtRuleTimeWindow.Text, 60);
  vRule.MessagePattern := txtRuleMessagePattern.Text;
  vRule.CountryCode := txtRuleCountryCode.Text;
  case cmbRuleAction.ItemIndex of
    0:
      vRule.ActionType := raDeny;
    1:
      vRule.ActionType := raAllow;
    2:
      vRule.ActionType := raBan;
    3:
      vRule.ActionType := raLog;
  end;
  vRule.BanDurationSec := StrToIntDef(txtRuleBanDuration.Text, 300);
  lbRules.Items.Add(vRule.Name);
  DoLog('Rule added: ' + vRule.Name);
end;

procedure TfrmFirewallDemo.btnRemoveRuleClick(Sender: TObject);
var
  vIdx: Integer;
begin
  vIdx := lbRules.ItemIndex;
  if vIdx >= 0 then
  begin
    DoLog('Rule removed: ' + lbRules.Items[vIdx]);
    Firewall.CustomRules.Rules.Delete(vIdx);
    lbRules.Items.Delete(vIdx);
  end;
end;

// --- Bot Detection ---

procedure TfrmFirewallDemo.chkBotDetectionClick(Sender: TObject);
begin
  Firewall.BotDetection.Enabled := chkBotDetection.Checked;
  DoLog('Bot Detection ' + IfThen(chkBotDetection.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyBotDetectionClick(Sender: TObject);
begin
  Firewall.BotDetection.KnownBotsFile := txtKnownBotsFile.Text;
  Firewall.BotDetection.CacheDurationSec :=
    StrToIntDef(txtCacheDuration.Text, 3600);
  Firewall.BotDetection.DNSTimeoutMS := StrToIntDef(txtDNSTimeout.Text, 2000);
  Firewall.BotDetection.Enabled := chkBotDetection.Checked;
  DoLog('Bot Detection settings: CacheDuration=' +
    IntToStr(Firewall.BotDetection.CacheDurationSec) + 's, DNSTimeout=' +
    IntToStr(Firewall.BotDetection.DNSTimeoutMS) + 'ms');
end;

procedure TfrmFirewallDemo.btnLoadKnownBotsClick(Sender: TObject);
begin
  OpenDialog1.Filter := 'All files (*.*)|*.*';
  if OpenDialog1.Execute then
  begin
    txtKnownBotsFile.Text := OpenDialog1.FileName;
    Firewall.BotDetection.KnownBotsFile := OpenDialog1.FileName;
    DoLog('Known Bots file: ' + ExtractFileName(OpenDialog1.FileName));
  end;
end;

procedure TfrmFirewallDemo.chkReverseDNSClick(Sender: TObject);
begin
  Firewall.BotDetection.ReverseDNS.Enabled := chkReverseDNS.Checked;
  DoLog('Reverse DNS verification ' + IfThen(chkReverseDNS.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.chkDatacenterClick(Sender: TObject);
begin
  Firewall.BotDetection.Datacenter.Enabled := chkDatacenter.Checked;
  DoLog('Datacenter detection ' + IfThen(chkDatacenter.Checked, 'enabled',
    'disabled'));
end;

procedure TfrmFirewallDemo.btnLoadASNClick(Sender: TObject);
begin
  OpenDialog1.Filter := 'All files (*.*)|*.*';
  if OpenDialog1.Execute then
  begin
    txtASNFile.Text := OpenDialog1.FileName;
    Firewall.BotDetection.Datacenter.ASNFile := OpenDialog1.FileName;
    DoLog('ASN/CIDR file: ' + ExtractFileName(OpenDialog1.FileName));
  end;
end;

procedure TfrmFirewallDemo.chkDNSBLClick(Sender: TObject);
begin
  Firewall.BotDetection.DNSBL.Enabled := chkDNSBL.Checked;
  DoLog('DNSBL ' + IfThen(chkDNSBL.Checked, 'enabled', 'disabled'));
end;

procedure TfrmFirewallDemo.btnApplyDNSBLClick(Sender: TObject);
begin
  Firewall.BotDetection.DNSBL.Zones.Assign(memoDNSBLZones.Lines);
  DoLog('DNSBL zones updated: ' + IntToStr(memoDNSBLZones.Lines.Count) +
    ' entries');
end;

procedure TfrmFirewallDemo.btnClassifyIPClick(Sender: TObject);
var
  vClass: TsgcBotClassification;
begin
  if txtTestIP.Text <> '' then
  begin
    vClass := Firewall.GetBotClassification(txtTestIP.Text);
    lblBotResult.Caption := 'Result: ' + BotClassificationToStr(vClass);
    DoLog('Classify ' + txtTestIP.Text + ' -> ' +
      BotClassificationToStr(vClass));
  end;
end;

procedure TfrmFirewallDemo.FirewallBotDetected(Sender: TObject;
  const aIP: string; aClassification: TsgcBotClassification;
  const aBotName: string);
begin
  DoLog('[BOT] ' + aIP + ' -> ' + BotClassificationToStr(aClassification) +
    IfThen(aBotName <> '', ' (' + aBotName + ')', ''));
end;

// --- Stats Timer ---

procedure TfrmFirewallDemo.tmrStatsTimer(Sender: TObject);
begin
  if Assigned(Firewall) then
  begin
    lblStatConnections.Caption := 'Active Connections: ' +
      IntToStr(Firewall.Stats.ActiveConnections);
    lblStatTotalConn.Caption := 'Total Connections: ' +
      IntToStr(Firewall.Stats.TotalConnections);
    lblStatBlocked.Caption := 'Total Blocked: ' +
      IntToStr(Firewall.Stats.TotalBlocked);
    lblStatMessages.Caption := 'Total Messages: ' +
      IntToStr(Firewall.Stats.TotalMessages);
    lblStatViolations.Caption := 'Total Violations: ' +
      IntToStr(Firewall.Stats.TotalViolations);
    lblStatSQLi.Caption := 'SQL Injection: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvSQLInjection));
    lblStatXSS.Caption := 'XSS: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvXSS));
    lblStatFlood.Caption := 'Flood: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvFlood));
    lblStatGeoIP.Caption := 'GeoIP: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvGeoIP));
    lblStatPathTraversal.Caption := 'Path Traversal: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvPathTraversal));
    lblStatCmdInj.Caption := 'Command Injection: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvCommandInjection));
    lblStatPayload.Caption := 'Payload Size: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvPayloadSize));
    lblStatThreatScore.Caption := 'Threat Score Bans: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvThreatScore));
    lblStatCustomRule.Caption := 'Custom Rules: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvCustomRule));
    lblStatBot.Caption := 'Bots: ' +
      IntToStr(Firewall.Stats.GetViolationCount(fvBot));
  end;
end;

end.
```

