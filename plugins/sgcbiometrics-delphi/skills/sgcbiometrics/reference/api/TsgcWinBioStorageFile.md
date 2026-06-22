# TsgcWinBioStorageFile

unit: sgcBiometrics

Add `sgcBiometrics` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `StorageOptions: TsgcBiometrics_Storage_Options` | [TsgcBiometrics_Storage_Options](../types/TsgcBiometrics_Storage_Options.md) | `__property TsgcBiometrics_Storage_Options * StorageOptions;` |
| `FileOptions: TsgcBiometrics_Storage_File_Options` | [TsgcBiometrics_Storage_File_Options](../types/TsgcBiometrics_Storage_File_Options.md) | `__property TsgcBiometrics_Storage_File_Options * FileOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAddDatabase: TsgcWinBioDatabaseAddDatabaseEvent` | [TsgcWinBioDatabaseAddDatabaseEvent](../types/TsgcWinBioDatabaseAddDatabaseEvent.md) | `__property TsgcWinBioDatabaseAddDatabaseEvent OnAddDatabase;` |
| `OnRemoveDatabase: TsgcWinBioDatabaseRemoveDatabaseEvent` | [TsgcWinBioDatabaseRemoveDatabaseEvent](../types/TsgcWinBioDatabaseRemoveDatabaseEvent.md) | `__property TsgcWinBioDatabaseRemoveDatabaseEvent OnRemoveDatabase;` |
| `OnAddUnit: TsgcWinBioDatabaseAddUnitEvent` | [TsgcWinBioDatabaseAddUnitEvent](../types/TsgcWinBioDatabaseAddUnitEvent.md) | `__property TsgcWinBioDatabaseAddUnitEvent OnAddUnit;` |
| `OnRemoveUnit: TsgcWinBioDatabaseRemoveUnitEvent` | [TsgcWinBioDatabaseRemoveUnitEvent](../types/TsgcWinBioDatabaseRemoveUnitEvent.md) | `__property TsgcWinBioDatabaseRemoveUnitEvent OnRemoveUnit;` |
| `OnError: TsgcWinBioDatabaseErrorEvent` | [TsgcWinBioDatabaseErrorEvent](../types/TsgcWinBioDatabaseErrorEvent.md) | `__property TsgcWinBioDatabaseErrorEvent OnError;` |

## Methods

Delphi

```pascal
function GetFilePath(aDatabaseId: String): String;
function GetConnectionString: String;
function GetStorageType: Cardinal;
procedure AddDatabase(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
procedure RemoveDatabase(const aDatabaseId: WINBIO_UUID);
procedure AddUnit(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
procedure RemoveUnit(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
function StorageExists: Boolean;
procedure SetBiometricType(aBiometricType: WINBIO_BIOMETRIC_TYPE);
```

C++Builder

```cpp
UnicodeString __fastcall GetFilePath(UnicodeString aDatabaseId);
UnicodeString __fastcall GetConnectionString();
unsigned int __fastcall GetStorageType();
void __fastcall AddDatabase(const WINBIO_UUID aDatabaseId, const int aUnitId);
void __fastcall RemoveDatabase(const WINBIO_UUID aDatabaseId);
void __fastcall AddUnit(const WINBIO_UUID aDatabaseId, const int aUnitId);
void __fastcall RemoveUnit(const WINBIO_UUID aDatabaseId, const int aUnitId);
bool __fastcall StorageExists();
void __fastcall SetBiometricType(WINBIO_BIOMETRIC_TYPE aBiometricType);
```

