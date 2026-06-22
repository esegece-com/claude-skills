# TsgcWSPClient_Dataset - Example

Usage of `TsgcWSPClient_Dataset` extracted from the **02.WebSocket_Protocols/05.DataSet_Quotes_Protocol** demo. See the full project for context.

API reference: [TsgcWSPClient_Dataset](../reference/api/TsgcWSPClient_Dataset.md)
Source demo: `02.WebSocket_Protocols/05.DataSet_Quotes_Protocol` (file `fClient.pas`)

```pascal
procedure TfrmClientQuotes.FormCreate(Sender: TObject);
  begin
  WSPClient_dataset.Dataset := DMQuotes.cdsQuotes;
  end;

```

