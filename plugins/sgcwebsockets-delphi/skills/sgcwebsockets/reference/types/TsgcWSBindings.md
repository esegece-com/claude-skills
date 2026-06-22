# TsgcWSBindings

kind: class
unit: sgcWebSocket_Server_Base

## Methods

```pascal
procedure Clear;
procedure NewBinding(const aHost: string; const aPort: Integer; const aParameters: string = ''; const aSSL: Boolean = False; const aSSLHash: String = ''; const aIPVersion: TwsIPVersion = ipV4; const aCertStoreName: String = '');
function GetURL(const aIndex: Integer): String;
```

