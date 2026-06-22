# Version history

Changes per sgcBiometrics release, newest first. Source: history.txt.

*******************************************************

 sgcBiometrics

*******************************************************

 [*] : Bug
 [+] : New
 [-] : Deleted
 [/] : Breaking changes

Versions
--------

## 2.4.0: 2026 February

 [*] : Fixed memory leak in DoCaptureSample where oUnitId and oSize were never freed.
 [*] : Fixed FillChar called on uninitialized pointers in DoReadCaptureSampleResult (WINBIO_E_BAD_CAPTURE branch).
 [*] : Fixed token handle leak in GetCurrentUserIdentity when GetTokenInformation fails.
 [*] : Fixed memory leak in DoEnumEnrollments where oIdentity was allocated outside Try..Finally block.
 [*] : Fixed Dispose(nil) crash in destructor when FDatabaseId was never allocated.
 [*] : Fixed WinBioFree not called on API-returned arrays in DoEnumBiometricUnits, DoEnumDatabases, StorageExists, GetDeviceInstanceId, and GetDeviceInstanceIds.
 [*] : Fixed potentially infinite loop in DoEnrollCapture when sensor keeps returning bad captures.
 [*] : Fixed registry key deletion while iterating in DoRemoveDatabase.
 [*] : Fixed premature break in registry key enumeration loops when non-numeric key names encountered.
 [*] : Fixed TsgcWinBioUsersINI properties not published (not visible in Object Inspector).
 [*] : Fixed duplicate error code constant CS_ERROR_CODE_ADD_UNIT (same value as CS_ERROR_CODE_ADD_DB).
 [*] : Fixed unnecessary inherited calls on abstract methods in TsgcBiometrics_WinBio_Users_INI.
 [*] : Fixed missing nil check on UserData in WinbioAsyncResultCallback.



## 2.3.0: 2025 September

 [+] : Added support for Rad Studio 13 Florence




## 2.2.1: 2024 August

 [*] : Fixed Bug Facial Component was not working when Optimization Compiler was enabled.




## 2.2.0: 2023 November

 [+] : Added support for Rad Studio 12 Athens




## 2.1.0: 2021 September

 [+] : Added support for Rad Studio 11 Alexandria
 [+] : New property RunsAsConsole, enable if your application runs as console to allow asynchronous processing.

 [*] : Fixed Bug when compiling runtime package when optimization option was enabled.



## 2.0.0: 2021 January

 [+] : New Component TsgcWinBioFacial which implements Facial Recognition, Identification and Presence Monitor.
 [+] : New Demo "Facial" which shows the main features of new facial recognition component.
 [+] : New overloaded method InitializeSensors(aTimeout) allows to wait till all sensors are initialized when Asynchronous mode is enabled.
 [+] : New method "EnumDatabases" to get all databases. The database data will be available OnEnumDatabase event.

 [*] : Fixed Bug when calling SessionClose in Asynchronous mode, the event was called twice.
 [*] : Fixed Bug if StorageFile.FileOptions.Path didn't ends with "\", the database was not created.


## 1.5.0: 2020 June

 [+] : Added support for Rad Studio 10.4 Sydney


## 1.4.0: 2020 January

 [+] : New method EnumEnrollments which retrieves the biometric sub-factors enrolled for a specified identity and biometric unit.
 [+] : New event OnEnumEnrollments called as a response of EnumEnrollments.
 [+] : New Component TsgcWinBioUsersINI which allows associate users to fingerprints.
 [+] : Updated demo to show fingerprint with CaptureSample method.

 [/] : aFirstPixel parameter of OnCaptureSample event is now PByte (before was Byte).


## 1.3.0: 2019 October

 [+] : New Property Asynchronous, if enabled, allows to process events asynchronously (application doesn't blocks till user action).
 [+] : New Method to delete biometric templates.
 [+] : New Event which is called when a template is deleted.


## 1.2.0: 2019 May

 [+] : Added support for Rad Studio 10.3 Rio.

 [*] : Fixed Bug compiling package for Delphi 7 and 2007.


## 1.1.0: 2018 May

 [+] : Added Code as New parameter OnError Event.
 [+] : New Method CaptureSample, allows an application to capture raw biometric data
 [+] : New Event OnCaptureSample, if result of CaptureSample method is successful, allows to manage biometric data (like save to an image).
 [+] : New Event OnCaptureSampleReject, if result of CaptureSample method is not successful, returns reject error.

 [*] : Minor bugs and fixes.


## 1.0.0: 2018 April

 [+] : New Component TsgcWinBioFingerPrint, allows to use FingerPrint sensor
 [+] : New Component TsgcWinBioStorageFile, allows to create a private sensor pool and store biometric data in a file.


