# TIdSSLSocket

kind: class
unit: IdSSLOpenSSL

## Properties

| Delphi | Type |
| --- | --- |
| `PeerCert: TIdX509 (read-only)` | [TIdX509](./TIdX509.md) |
| `Cipher: TIdSSLCipher (read-only)` | [TIdSSLCipher](./TIdSSLCipher.md) |
| `HostName: String (read-only)` | `String` |
| `IO: Boolean` | `Boolean` |
| `IOSSL_HandShake: Boolean` | `Boolean` |
| `X509Checks: TIdSSLX509Checks` | [TIdSSLX509Checks](./TIdSSLX509Checks.md) |
| `ALPNProtocol: = vOffSet + vLength (read-only)` |  |

## Events

| Delphi | Type |
| --- | --- |
| `OnALPNSelect: TALPNSelectEvent` | [TALPNSelectEvent](./TALPNSelectEvent.md) |
| `OnSSLIO_HandShake: TsgcSSLIO_HandShakeEvent` | [TsgcSSLIO_HandShakeEvent](./TsgcSSLIO_HandShakeEvent.md) |
| `OnSSLIO_Write: TsgcSSLIO_WriteEvent` | [TsgcSSLIO_WriteEvent](./TsgcSSLIO_WriteEvent.md) |
| `OnSSLIO_Read: TsgcSSLIO_ReadEvent` | [TsgcSSLIO_ReadEvent](./TsgcSSLIO_ReadEvent.md) |

## Methods

```pascal
procedure DoIOSSL_HandShake(const aBuffer: TIdBytes);
procedure Accept(const pHandle: TIdStackSocketHandle);
procedure Connect(const pHandle: TIdStackSocketHandle);
function Send(const ABuffer: TIdBytes; AOffset, ALength: Integer): Integer;
function Recv(var ABuffer: TIdBytes): Integer;
function GetSessionID: TIdSSLByteArray;
function GetSessionIDAsString: String;
procedure SetCipherList(CipherList: String);
```

