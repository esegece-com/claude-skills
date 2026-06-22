# TIdDateTimeStamp

unit: IdDateTimeStamp

Add `IdDateTimeStamp` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AsISO8601Calendar: String (read-only)` | `String` | `__property UnicodeString AsISO8601Calendar /* read-only */;` |
| `AsISO8601Ordinal: String (read-only)` | `String` | `__property UnicodeString AsISO8601Ordinal /* read-only */;` |
| `AsISO8601Week: String (read-only)` | `String` | `__property UnicodeString AsISO8601Week /* read-only */;` |
| `AsRFC822: String (read-only)` | `String` | `__property UnicodeString AsRFC822 /* read-only */;` |
| `AsTDateTime: TDateTime (read-only)` | `TDateTime` | `__property System::TDateTime AsTDateTime /* read-only */;` |
| `AsTTimeStamp: TIdDateTimeStamp (read-only)` | [TIdDateTimeStamp](../types/TIdDateTimeStamp.md) | `__property TIdDateTimeStamp * AsTTimeStamp /* read-only */;` |
| `AsTimeOfDay: String (read-only)` | `String` | `__property UnicodeString AsTimeOfDay /* read-only */;` |
| `BeatOfDay: Integer (read-only)` | `Integer` | `__property int BeatOfDay /* read-only */;` |
| `Day: Integer` | `Integer` | `__property int Day;` |
| `DaysInYear: Integer (read-only)` | `Integer` | `__property int DaysInYear /* read-only */;` |
| `DayOfMonth: Integer (read-only)` | `Integer` | `__property int DayOfMonth /* read-only */;` |
| `DayOfWeek: Integer (read-only)` | `Integer` | `__property int DayOfWeek /* read-only */;` |
| `DayOfWeekName: String (read-only)` | `String` | `__property UnicodeString DayOfWeekName /* read-only */;` |
| `DayOfWeekShortName: String (read-only)` | `String` | `__property UnicodeString DayOfWeekShortName /* read-only */;` |
| `HourOf12Day: Integer (read-only)` | `Integer` | `__property int HourOf12Day /* read-only */;` |
| `HourOf24Day: Integer (read-only)` | `Integer` | `__property int HourOf24Day /* read-only */;` |
| `IsLeapYear: Boolean (read-only)` | `Boolean` | `__property bool IsLeapYear /* read-only */;` |
| `IsMorning: Boolean (read-only)` | `Boolean` | `__property bool IsMorning /* read-only */;` |
| `Millisecond: Integer` | `Integer` | `__property int Millisecond;` |
| `MinuteOfDay: Integer (read-only)` | `Integer` | `__property int MinuteOfDay /* read-only */;` |
| `MinuteOfHour: Integer (read-only)` | `Integer` | `__property int MinuteOfHour /* read-only */;` |
| `MonthOfYear: Integer (read-only)` | `Integer` | `__property int MonthOfYear /* read-only */;` |
| `MonthName: String (read-only)` | `String` | `__property UnicodeString MonthName /* read-only */;` |
| `MonthShortName: String (read-only)` | `String` | `__property UnicodeString MonthShortName /* read-only */;` |
| `Second: Integer` | `Integer` | `__property int Second;` |
| `SecondsInYear: Integer (read-only)` | `Integer` | `__property int SecondsInYear /* read-only */;` |
| `SecondOfMinute: Integer (read-only)` | `Integer` | `__property int SecondOfMinute /* read-only */;` |
| `TimeZone: Integer` | `Integer` | `__property int TimeZone;` |
| `TimeZoneHour: Integer (read-only)` | `Integer` | `__property int TimeZoneHour /* read-only */;` |
| `TimeZoneMinutes: Integer (read-only)` | `Integer` | `__property int TimeZoneMinutes /* read-only */;` |
| `TimeZoneAsString: String (read-only)` | `String` | `__property UnicodeString TimeZoneAsString /* read-only */;` |
| `Year: Integer` | `Integer` | `__property int Year;` |
| `WeekOfYear: Integer (read-only)` | `Integer` | `__property int WeekOfYear /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure AddDays(ANumber : UInt32);
procedure AddHours(ANumber : UInt32);
procedure AddMilliseconds(ANumber : UInt32);
procedure AddMinutes(ANumber : UInt32);
procedure AddMonths(ANumber : UInt32);
procedure AddSeconds(ANumber : UInt32);
procedure AddTDateTime(ADateTime : TDateTime);
procedure AddTIdDateTimeStamp(AIdDateTime : TIdDateTimeStamp);
procedure AddTTimeStamp(ATimeStamp : TIdDateTimeStamp);
procedure AddWeeks(ANumber : UInt32);
procedure AddYears(ANumber : UInt32);
function GetAsISO8601Calendar : String;
function GetAsISO8601Ordinal : String;
function GetAsISO8601Week : String;
function GetAsRFC822 : String;
function GetAsTDateTime : TDateTime;
function GetAsTTimeStamp : TIdDateTimeStamp;
function GetAsTimeOfDay : String;
function GetBeatOfDay : Integer;
function GetDaysInYear : Integer;
function GetDayOfMonth : Integer;
function GetDayOfWeek : Integer;
function GetDayOfWeekName : String;
function GetDayOfWeekShortName : String;
function GetHourOf12Day : Integer;
function GetHourOf24Day : Integer;
function GetIsMorning : Boolean;
function GetMinuteOfDay : Integer;
function GetMinuteOfHour : Integer;
function GetMonthOfYear : Integer;
function GetMonthName : String;
function GetMonthShortName : String;
function GetSecondsInYear : Integer;
function GetSecondOfMinute : Integer;
function GetTimeZoneAsString: String;
function GetTimeZoneHour: Integer;
function GetTimeZoneMinutes: Integer;
function GetWeekOfYear : Integer;
procedure SetFromDOSDateTime(ADate, ATime : Word);
procedure SetFromISO8601(AString : String);
procedure SetFromRFC822(AString : String);
procedure SetFromTDateTime(ADateTime : TDateTime);
procedure SetFromTTimeStamp(ATimeStamp : TIdDateTimeStamp);
procedure SetDay(ANumber : Integer);
procedure SetMillisecond(ANumber : Integer);
procedure SetSecond(ANumber : Integer);
procedure SetTimeZone(const Value: Integer);
procedure SetYear(ANumber : Integer);
procedure SubtractDays(ANumber : UInt32);
procedure SubtractHours(ANumber : UInt32);
procedure SubtractMilliseconds(ANumber : UInt32);
procedure SubtractMinutes(ANumber : UInt32);
procedure SubtractMonths(ANumber : UInt32);
procedure SubtractSeconds(ANumber : UInt32);
procedure SubtractTDateTime(ADateTime : TDateTime);
procedure SubtractTIdDateTimeStamp(AIdDateTime : TIdDateTimeStamp);
procedure SubtractTTimeStamp(ATimeStamp : TIdDateTimeStamp);
procedure SubtractWeeks(ANumber : UInt32);
procedure SubtractYears(ANumber : UInt32);
procedure Zero;
procedure ZeroDate;
procedure ZeroTime;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall AddDays(UInt32 ANumber);
void __fastcall AddHours(UInt32 ANumber);
void __fastcall AddMilliseconds(UInt32 ANumber);
void __fastcall AddMinutes(UInt32 ANumber);
void __fastcall AddMonths(UInt32 ANumber);
void __fastcall AddSeconds(UInt32 ANumber);
void __fastcall AddTDateTime(System::TDateTime ADateTime);
void __fastcall AddTIdDateTimeStamp(TIdDateTimeStamp * AIdDateTime);
void __fastcall AddTTimeStamp(TIdDateTimeStamp * ATimeStamp);
void __fastcall AddWeeks(UInt32 ANumber);
void __fastcall AddYears(UInt32 ANumber);
UnicodeString __fastcall GetAsISO8601Calendar();
UnicodeString __fastcall GetAsISO8601Ordinal();
UnicodeString __fastcall GetAsISO8601Week();
UnicodeString __fastcall GetAsRFC822();
System::TDateTime __fastcall GetAsTDateTime();
TIdDateTimeStamp * __fastcall GetAsTTimeStamp();
UnicodeString __fastcall GetAsTimeOfDay();
int __fastcall GetBeatOfDay();
int __fastcall GetDaysInYear();
int __fastcall GetDayOfMonth();
int __fastcall GetDayOfWeek();
UnicodeString __fastcall GetDayOfWeekName();
UnicodeString __fastcall GetDayOfWeekShortName();
int __fastcall GetHourOf12Day();
int __fastcall GetHourOf24Day();
bool __fastcall GetIsMorning();
int __fastcall GetMinuteOfDay();
int __fastcall GetMinuteOfHour();
int __fastcall GetMonthOfYear();
UnicodeString __fastcall GetMonthName();
UnicodeString __fastcall GetMonthShortName();
int __fastcall GetSecondsInYear();
int __fastcall GetSecondOfMinute();
UnicodeString __fastcall GetTimeZoneAsString();
int __fastcall GetTimeZoneHour();
int __fastcall GetTimeZoneMinutes();
int __fastcall GetWeekOfYear();
void __fastcall SetFromDOSDateTime(unsigned short ADate, unsigned short ATime);
void __fastcall SetFromISO8601(UnicodeString AString);
void __fastcall SetFromRFC822(UnicodeString AString);
void __fastcall SetFromTDateTime(System::TDateTime ADateTime);
void __fastcall SetFromTTimeStamp(TIdDateTimeStamp * ATimeStamp);
void __fastcall SetDay(int ANumber);
void __fastcall SetMillisecond(int ANumber);
void __fastcall SetSecond(int ANumber);
void __fastcall SetTimeZone(const int Value);
void __fastcall SetYear(int ANumber);
void __fastcall SubtractDays(UInt32 ANumber);
void __fastcall SubtractHours(UInt32 ANumber);
void __fastcall SubtractMilliseconds(UInt32 ANumber);
void __fastcall SubtractMinutes(UInt32 ANumber);
void __fastcall SubtractMonths(UInt32 ANumber);
void __fastcall SubtractSeconds(UInt32 ANumber);
void __fastcall SubtractTDateTime(System::TDateTime ADateTime);
void __fastcall SubtractTIdDateTimeStamp(TIdDateTimeStamp * AIdDateTime);
void __fastcall SubtractTTimeStamp(TIdDateTimeStamp * ATimeStamp);
void __fastcall SubtractWeeks(UInt32 ANumber);
void __fastcall SubtractYears(UInt32 ANumber);
void __fastcall Zero();
void __fastcall ZeroDate();
void __fastcall ZeroTime();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

