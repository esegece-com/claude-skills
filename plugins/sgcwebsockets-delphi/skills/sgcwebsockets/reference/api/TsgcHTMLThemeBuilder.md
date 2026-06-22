# TsgcHTMLThemeBuilder

unit: sgcHTML_ThemeBuilder

Add `sgcHTML_ThemeBuilder` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `PrimaryColor: string` | `string` | `__property UnicodeString PrimaryColor;` |
| `SecondaryColor: string` | `string` | `__property UnicodeString SecondaryColor;` |
| `SuccessColor: string` | `string` | `__property UnicodeString SuccessColor;` |
| `DangerColor: string` | `string` | `__property UnicodeString DangerColor;` |
| `WarningColor: string` | `string` | `__property UnicodeString WarningColor;` |
| `InfoColor: string` | `string` | `__property UnicodeString InfoColor;` |
| `BodyBackground: string` | `string` | `__property UnicodeString BodyBackground;` |
| `BodyColor: string` | `string` | `__property UnicodeString BodyColor;` |
| `CardBackground: string` | `string` | `__property UnicodeString CardBackground;` |
| `BorderColor: string` | `string` | `__property UnicodeString BorderColor;` |
| `FontFamily: string` | `string` | `__property UnicodeString FontFamily;` |
| `BorderRadius: string` | `string` | `__property UnicodeString BorderRadius;` |
| `Mode: TsgcHTMLThemeMode` | [TsgcHTMLThemeMode](../types/TsgcHTMLThemeMode.md) | `__property TsgcHTMLThemeMode * Mode;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function GetCSS: string;
procedure SetDarkDefaults;
procedure SetLightDefaults;
```

C++Builder

```cpp
UnicodeString __fastcall GetCSS();
void __fastcall SetDarkDefaults();
void __fastcall SetLightDefaults();
```

