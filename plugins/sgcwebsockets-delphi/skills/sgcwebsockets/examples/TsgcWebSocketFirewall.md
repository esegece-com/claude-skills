# TsgcWebSocketFirewall - Example

Usage of `TsgcWebSocketFirewall` extracted from the **04.WebSocket_Other_Samples/13.Firewall** demo. See the full project for context.

API reference: [TsgcWebSocketFirewall](../reference/api/TsgcWebSocketFirewall.md)
Source demo: `04.WebSocket_Other_Samples/13.Firewall` (file `uFirewallDemo.pas`)

```pascal
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

procedure TfrmFirewallDemo.chkSQLInjectionClick(Sender: TObject);
  begin
```

