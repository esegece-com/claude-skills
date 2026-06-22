# TsgcWSPClient_E2EE - Example

Usage of `TsgcWSPClient_E2EE` extracted from the **02.WebSocket_Protocols/12.E2EE** demo. See the full project for context.

API reference: [TsgcWSPClient_E2EE](../reference/api/TsgcWSPClient_E2EE.md)
Source demo: `02.WebSocket_Protocols/12.E2EE` (file `uClientE2EE.pas`)

```pascal
procedure TfrmClientE2EE.btnCreateGroupClick(Sender: TObject);
  begin
  E2EE.CreateGroup(txtGroupName.Text);
  end;

procedure TfrmClientE2EE.btnDeleteGroupClick(Sender: TObject);
  begin
  E2EE.DeleteGroup(txtGroupName.Text);
  end;

procedure TfrmClientE2EE.btnJoinGroupClick(Sender: TObject);
  begin
  E2EE.JoinGroup(txtGroupName.Text);
  end;

procedure TfrmClientE2EE.btnLeaveGroupClick(Sender: TObject);
  begin
  E2EE.LeaveGroup(txtGroupName.Text);
  end;

procedure TfrmClientE2EE.FormCreate(Sender: TObject);
  begin
  Randomize;
  txtUserId.Text := GetRandomUserId;
  E2EE.E2EE_Options.UserId := txtUserId.Text;
  end;

procedure TfrmClientE2EE.btnSendDirectMessageClick(Sender: TObject);
  begin
  if cboMessageTo.Text <> '' then
  begin
  E2EE.SendDirectMessage(cboMessageTo.Text, txtDirectMessage.Text);
  txtDirectMessage.Text := '';
  end;
  end;

procedure TfrmClientE2EE.btnSendGroupMessageClick(Sender: TObject);
  begin
  E2EE.SendGroupMessage(txtGroupName.Text, txtGroupMessage.Text);
  end;

```

