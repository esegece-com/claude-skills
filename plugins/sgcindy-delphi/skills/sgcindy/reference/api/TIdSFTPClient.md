# TIdSFTPClient

unit: IdSFTPClient

Add `IdSFTPClient` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: Word` | `Word` | `__property unsigned short Port;` |
| `Authentication: TIdSSHAuthentication` | [TIdSSHAuthentication](../types/TIdSSHAuthentication.md) | `__property TIdSSHAuthentication * Authentication;` |
| `Algorithms: TIdSSHAlgorithms` | [TIdSSHAlgorithms](../types/TIdSSHAlgorithms.md) | `__property TIdSSHAlgorithms * Algorithms;` |
| `KeepAlive: TIdSSHKeepAlive` | [TIdSSHKeepAlive](../types/TIdSSHKeepAlive.md) | `__property TIdSSHKeepAlive * KeepAlive;` |
| `SSHOptions: TIdSSHOptions` | [TIdSSHOptions](../types/TIdSSHOptions.md) | `__property TIdSSHOptions * SSHOptions;` |
| `SFTPBufferSize: Cardinal` | `Cardinal` | `__property unsigned int SFTPBufferSize;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSFTPConnect: TIdSFTPConnectEvent` | [TIdSFTPConnectEvent](../types/TIdSFTPConnectEvent.md) | `__property TIdSFTPConnectEvent OnSFTPConnect;` |
| `OnSFTPDisconnect: TIdSFTPDisconnectEvent` | [TIdSFTPDisconnectEvent](../types/TIdSFTPDisconnectEvent.md) | `__property TIdSFTPDisconnectEvent OnSFTPDisconnect;` |
| `OnSFTPError: TIdSFTPErrorEvent` | [TIdSFTPErrorEvent](../types/TIdSFTPErrorEvent.md) | `__property TIdSFTPErrorEvent OnSFTPError;` |
| `OnSFTPProgress: TIdSFTPProgressEvent` | [TIdSFTPProgressEvent](../types/TIdSFTPProgressEvent.md) | `__property TIdSFTPProgressEvent OnSFTPProgress;` |
| `OnSFTPDirectoryList: TIdSFTPDirectoryListEvent` | [TIdSFTPDirectoryListEvent](../types/TIdSFTPDirectoryListEvent.md) | `__property TIdSFTPDirectoryListEvent OnSFTPDirectoryList;` |
| `OnSFTPStatus: TIdSFTPStatusEvent` | [TIdSFTPStatusEvent](../types/TIdSFTPStatusEvent.md) | `__property TIdSFTPStatusEvent OnSFTPStatus;` |
| `OnSSHAuthentication: TIdSSHAuthenticationEvent` | [TIdSSHAuthenticationEvent](../types/TIdSSHAuthenticationEvent.md) | `__property TIdSSHAuthenticationEvent OnSSHAuthentication;` |
| `OnSSHHostKey: TIdSSHHostKeyEvent` | [TIdSSHHostKeyEvent](../types/TIdSSHHostKeyEvent.md) | `__property TIdSSHHostKeyEvent OnSSHHostKey;` |
| `OnSSHAuthBanner: TIdSSHAuthBannerEvent` | [TIdSSHAuthBannerEvent](../types/TIdSSHAuthBannerEvent.md) | `__property TIdSSHAuthBannerEvent OnSSHAuthBanner;` |
| `OnSSHKeyboardInteractive: TIdSSHKeyboardInteractiveEvent` | [TIdSSHKeyboardInteractiveEvent](../types/TIdSSHKeyboardInteractiveEvent.md) | `__property TIdSSHKeyboardInteractiveEvent OnSSHKeyboardInteractive;` |

## Methods

Delphi

```pascal
procedure Connect;
procedure Disconnect;
function Active: Boolean;
procedure Get(const aRemotePath, aLocalPath: string);
procedure Put(const aLocalPath, aRemotePath: string);
procedure Delete(const aRemotePath: string);
procedure Rename(const aOldPath, aNewPath: string);
function ListDirectory(const aRemotePath: string): TIdSFTPDirectoryItems;
procedure MakeDirectory(const aRemotePath: string);
procedure RemoveDirectory(const aRemotePath: string);
function Stat(const aRemotePath: string): TIdSFTPFileAttributes;
function LStat(const aRemotePath: string): TIdSFTPFileAttributes;
procedure SetStat(const aRemotePath: string; const aAttrs: TIdSFTPFileAttributes);
function FileExists(const aRemotePath: string): Boolean;
function DirectoryExists(const aRemotePath: string): Boolean;
function FileSize(const aRemotePath: string): Int64;
function RealPath(const aPath: string): string;
function ReadLink(const aPath: string): string;
procedure Symlink(const aTargetPath, aLinkPath: string);
function GetCurrentDirectory: string;
function GetFileAsString(const aRemotePath: string): string;
procedure PutFileFromString(const aContent, aRemotePath: string);
```

C++Builder

```cpp
void __fastcall Connect();
void __fastcall Disconnect();
bool __fastcall Active();
void __fastcall Get(const UnicodeString aRemotePath, const UnicodeString aLocalPath);
void __fastcall Put(const UnicodeString aLocalPath, const UnicodeString aRemotePath);
void __fastcall Delete(const UnicodeString aRemotePath);
void __fastcall Rename(const UnicodeString aOldPath, const UnicodeString aNewPath);
TIdSFTPDirectoryItems * __fastcall ListDirectory(const UnicodeString aRemotePath);
void __fastcall MakeDirectory(const UnicodeString aRemotePath);
void __fastcall RemoveDirectory(const UnicodeString aRemotePath);
TIdSFTPFileAttributes * __fastcall Stat(const UnicodeString aRemotePath);
TIdSFTPFileAttributes * __fastcall LStat(const UnicodeString aRemotePath);
void __fastcall SetStat(const UnicodeString aRemotePath, const TIdSFTPFileAttributes * aAttrs);
bool __fastcall FileExists(const UnicodeString aRemotePath);
bool __fastcall DirectoryExists(const UnicodeString aRemotePath);
long long __fastcall FileSize(const UnicodeString aRemotePath);
UnicodeString __fastcall RealPath(const UnicodeString aPath);
UnicodeString __fastcall ReadLink(const UnicodeString aPath);
void __fastcall Symlink(const UnicodeString aTargetPath, const UnicodeString aLinkPath);
UnicodeString __fastcall GetCurrentDirectory();
UnicodeString __fastcall GetFileAsString(const UnicodeString aRemotePath);
void __fastcall PutFileFromString(const UnicodeString aContent, const UnicodeString aRemotePath);
```

