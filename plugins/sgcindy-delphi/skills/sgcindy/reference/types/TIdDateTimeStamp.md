# TIdDateTimeStamp

kind: class
unit: IdDateTimeStamp

## Properties

| Delphi | Type |
| --- | --- |
| `AsISO8601Calendar: String (read-only)` | `String` |
| `AsISO8601Ordinal: String (read-only)` | `String` |
| `AsISO8601Week: String (read-only)` | `String` |
| `AsRFC822: String (read-only)` | `String` |
| `AsTDateTime: TDateTime (read-only)` | `TDateTime` |
| `AsTTimeStamp: TIdDateTimeStamp (read-only)` | [TIdDateTimeStamp](./TIdDateTimeStamp.md) |
| `AsTimeOfDay: String (read-only)` | `String` |
| `BeatOfDay: Integer (read-only)` | `Integer` |
| `Day: Integer` | `Integer` |
| `DaysInYear: Integer (read-only)` | `Integer` |
| `DayOfMonth: Integer (read-only)` | `Integer` |
| `DayOfWeek: Integer (read-only)` | `Integer` |
| `DayOfWeekName: String (read-only)` | `String` |
| `DayOfWeekShortName: String (read-only)` | `String` |
| `HourOf12Day: Integer (read-only)` | `Integer` |
| `HourOf24Day: Integer (read-only)` | `Integer` |
| `IsLeapYear: Boolean (read-only)` | `Boolean` |
| `IsMorning: Boolean (read-only)` | `Boolean` |
| `Millisecond: Integer` | `Integer` |
| `MinuteOfDay: Integer (read-only)` | `Integer` |
| `MinuteOfHour: Integer (read-only)` | `Integer` |
| `MonthOfYear: Integer (read-only)` | `Integer` |
| `MonthName: String (read-only)` | `String` |
| `MonthShortName: String (read-only)` | `String` |
| `Second: Integer` | `Integer` |
| `SecondsInYear: Integer (read-only)` | `Integer` |
| `SecondOfMinute: Integer (read-only)` | `Integer` |
| `TimeZone: Integer` | `Integer` |
| `TimeZoneHour: Integer (read-only)` | `Integer` |
| `TimeZoneMinutes: Integer (read-only)` | `Integer` |
| `TimeZoneAsString: String (read-only)` | `String` |
| `Year: Integer` | `Integer` |
| `WeekOfYear: Integer (read-only)` | `Integer` |
| `Version: string (read-only)` | `string` |

## Methods

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

