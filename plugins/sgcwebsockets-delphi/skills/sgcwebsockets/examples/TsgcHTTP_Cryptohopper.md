# TsgcHTTP_Cryptohopper - Example

Usage of `TsgcHTTP_Cryptohopper` extracted from the **50.Other/03.Cryptohopper** demo. See the full project for context.

API reference: [TsgcHTTP_Cryptohopper](../reference/api/TsgcHTTP_Cryptohopper.md)
Source demo: `50.Other/03.Cryptohopper` (file `FCryptohopper.pas`)

```pascal
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
```

