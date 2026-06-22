# TsgcBiometrics_WinBio_Storage

kind: class
unit: sgcBiometrics_WinBio_Storage

## Properties

| Delphi | Type |
| --- | --- |
| `StorageOptions: TsgcBiometrics_Storage_Options` | [TsgcBiometrics_Storage_Options](./TsgcBiometrics_Storage_Options.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnAddDatabase: TsgcWinBioDatabaseAddDatabaseEvent` | [TsgcWinBioDatabaseAddDatabaseEvent](./TsgcWinBioDatabaseAddDatabaseEvent.md) |
| `OnRemoveDatabase: TsgcWinBioDatabaseRemoveDatabaseEvent` | [TsgcWinBioDatabaseRemoveDatabaseEvent](./TsgcWinBioDatabaseRemoveDatabaseEvent.md) |
| `OnAddUnit: TsgcWinBioDatabaseAddUnitEvent` | [TsgcWinBioDatabaseAddUnitEvent](./TsgcWinBioDatabaseAddUnitEvent.md) |
| `OnRemoveUnit: TsgcWinBioDatabaseRemoveUnitEvent` | [TsgcWinBioDatabaseRemoveUnitEvent](./TsgcWinBioDatabaseRemoveUnitEvent.md) |
| `OnError: TsgcWinBioDatabaseErrorEvent` | [TsgcWinBioDatabaseErrorEvent](./TsgcWinBioDatabaseErrorEvent.md) |

## Methods

```pascal
procedure AddDatabase(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
procedure RemoveDatabase(const aDatabaseId: WINBIO_UUID);
procedure AddUnit(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
procedure RemoveUnit(const aDatabaseId: WINBIO_UUID; const aUnitId: integer);
function StorageExists: Boolean;
procedure SetBiometricType(aBiometricType: WINBIO_BIOMETRIC_TYPE);
```

