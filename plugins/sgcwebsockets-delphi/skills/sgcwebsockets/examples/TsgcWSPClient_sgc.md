# TsgcWSPClient_sgc - Example

Usage of `TsgcWSPClient_sgc` extracted from the **02.WebSocket_Protocols/01.SGC_Generic_PubSub_Protocol** demo. See the full project for context.

API reference: [TsgcWSPClient_sgc](../reference/api/TsgcWSPClient_sgc.md)
Source demo: `02.WebSocket_Protocols/01.SGC_Generic_PubSub_Protocol` (file `uClientPROTOCOL.pas`)

```pascal
procedure TfrmClientPROTOCOL.btnCommitClick(Sender: TObject);
  begin
  WSPPROTOCOL.Commit(txtTransactionChannel.Text);
  end;

procedure TfrmClientPROTOCOL.btnGetSessionClick(Sender: TObject);
  begin
  WSPProtocol.GetSession;
  end;

procedure TfrmClientPROTOCOL.btnNotifyClick(Sender: TObject);
  begin
  WSPProtocol.Notify(txtNotify.Text);
  end;

procedure TfrmClientPROTOCOL.btnSubscribeClick(Sender: TObject);
  begin
  WSPPROTOCOL.Subscribe(txtChannel.text);
  end;

procedure TfrmClientPROTOCOL.btnStartClick(Sender: TObject);
  begin
  case cboQoSLevel.ItemIndex of
  0: WSPPROTOCOL.QoS.Level := qosLevel0;
  1: WSPPROTOCOL.QoS.Level := qosLevel1;
  2: WSPPROTOCOL.QoS.Level := qosLevel2;
  end;

procedure TfrmClientPROTOCOL.btnUnsubscribeClick(Sender: TObject);
  begin
  WSPPROTOCOL.UnSubscribe(txtChannel.text);
  end;

procedure TfrmClientPROTOCOL.btnRPCClick(Sender: TObject);
  begin
  WSPPROTOCOL.RPC(txtRPCID.Text, txtRPCMethod.Text, txtRPCParams.Text);
  end;

procedure TfrmClientPROTOCOL.btnPublishClick(Sender: TObject);
  begin
  WSPPROTOCOL.Publish(txtPublishMessage.Text, txtPublishChannel.Text, '', TwsQueue(cboQueueLevel.ItemIndex));
  end;

procedure TfrmClientPROTOCOL.btnRollBackClick(Sender: TObject);
  begin
  WSPPROTOCOL.RollBack(txtTransactionChannel.Text);
  end;

procedure TfrmClientPROTOCOL.btnStartTransactionClick(Sender: TObject);
  begin
  WSPPROTOCOL.StartTransaction(txtTransactionChannel.Text);
  end;

procedure TfrmClientPROTOCOL.btnUnSubscribeAllClick(Sender: TObject);
  begin
  WSPPROTOCOL.UnSubscribeAll;
  end;

```

