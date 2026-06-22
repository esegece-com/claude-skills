# TsgcWSPServer_Dataset - Example

Usage of `TsgcWSPServer_Dataset` extracted from the **02.WebSocket_Protocols/05.DataSet_Quotes_Protocol** demo. See the full project for context.

API reference: [TsgcWSPServer_Dataset](../reference/api/TsgcWSPServer_Dataset.md)
Source demo: `02.WebSocket_Protocols/05.DataSet_Quotes_Protocol` (file `fServer.pas`)

```pascal
procedure TfrmServer.FormCreate(Sender: TObject);
  begin
  dsQuotes.DataSet := DMQuotes.cdsQuotes;
  WSPServer_dataset.Dataset := DMQuotes.cdsQuotes;
  btnStart.Click;
  end;

```

