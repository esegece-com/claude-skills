# TIdFTPBaseFileSystem

kind: class
unit: IdFTPBaseFileSystem

## Properties

| Delphi | Type |
| --- | --- |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
procedure ChangeDir(AContext : TIdFTPServerContextBase; var VDirectory: TIdFTPFileName);
procedure GetFileSize(AContext : TIdFTPServerContextBase; const AFilename: TIdFTPFileName; var VFileSize: Int64);
procedure GetFileDate(AContext : TIdFTPServerContextBase; const AFilename: TIdFTPFileName; var VFileDate: TDateTime);
procedure ListDirectory(AContext : TIdFTPServerContextBase; const APath: TIdFTPFileName; ADirectoryListing: TIdFTPListOutput; const ACmd, ASwitches : String);
procedure RenameFile(AContext : TIdFTPServerContextBase; const ARenameToFile: TIdFTPFileName);
procedure DeleteFile(AContext : TIdFTPServerContextBase; const APathName: TIdFTPFileName);
procedure RetrieveFile(AContext : TIdFTPServerContextBase; const AFileName: TIdFTPFileName; var VStream: TStream);
procedure StoreFile(AContext : TIdFTPServerContextBase; const AFileName: TIdFTPFileName; AAppend: Boolean; var VStream: TStream);
procedure MakeDirectory(AContext : TIdFTPServerContextBase; var VDirectory: TIdFTPFileName);
procedure RemoveDirectory(AContext : TIdFTPServerContextBase; var VDirectory: TIdFTPFileName);
procedure SetModifiedFileDate(AContext : TIdFTPServerContextBase; const AFileName: TIdFTPFileName; var VDateTime: TDateTime);
procedure GetCRCCalcStream(AContext : TIdFTPServerContextBase; const AFileName: TIdFTPFileName; var VStream : TStream);
procedure CombineFiles(AContext : TIdFTPServerContextBase; const ATargetFileName: TIdFTPFileName; AParts: TStrings);
procedure RemoveFreeNotification(AComponent: TComponent);
```

