# TsgcWSPClient_WAMP - Example

Usage of `TsgcWSPClient_WAMP` extracted from the **02.WebSocket_Protocols/04.WAMP_Protocol** demo. See the full project for context.

API reference: [TsgcWSPClient_WAMP](../reference/api/TsgcWSPClient_WAMP.md)
Source demo: `02.WebSocket_Protocols/04.WAMP_Protocol` (file `uClientWAMP.pas`)

```pascal
procedure TfrmClientWAMP.btnPrefixClick(Sender: TObject);
  begin
  WSPWAMP.Prefix(txtKey.Text, txtValue.Text);
  end;

procedure TfrmClientWAMP.btnSubscribeClick(Sender: TObject);
  begin
  WSPWAMP.Subscribe(txtTopicURI.text);
  end;

procedure TfrmClientWAMP.btnUnsubscribeClick(Sender: TObject);
  begin
  WSPWAMP.UnSubscribe(txtTopicURI.Text);
  end;

procedure TfrmClientWAMP.btnCallClick(Sender: TObject);
  begin
  WSPWAMP.Call(txtCallId.Text, txtProcURI.Text, txtArguments.Text);
  end;

procedure TfrmClientWAMP.btnCancelCallClick(Sender: TObject);
  begin
  WSPWAMP.CancelCall(txtProgressCallId.Text);
  end;

procedure TfrmClientWAMP.btnPublishClick(Sender: TObject);
  begin
  WSPWAMP.Publish(txtTopic.Text, txtEvent.Text);
  end;

procedure TfrmClientWAMP.btnProgressCallClick(Sender: TObject);
  begin
  WSPWAMP.Call(txtProgressCallId.Text, txtProgressProcURI.Text, txtProgressArguments.Text);
  end;

```

