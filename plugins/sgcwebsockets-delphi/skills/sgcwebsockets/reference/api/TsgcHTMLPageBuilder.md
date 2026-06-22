# TsgcHTMLPageBuilder

unit: sgcHTML_Component
Edition: All-Access

Add `sgcHTML_Component` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `DarkMode: Boolean` | `Boolean` | `__property bool DarkMode;` |
| `IncludeBootstrap: Boolean` | `Boolean` | `__property bool IncludeBootstrap;` |
| `CustomCSS: string` | `string` | `__property UnicodeString CustomCSS;` |
| `FooterText: string` | `string` | `__property UnicodeString FooterText;` |
| `SidebarBrand: string` | `string` | `__property UnicodeString SidebarBrand;` |
| `SidebarWidth: string` | `string` | `__property UnicodeString SidebarWidth;` |
| `SidebarDark: Boolean` | `Boolean` | `__property bool SidebarDark;` |
| `ShowSidebar: Boolean` | `Boolean` | `__property bool ShowSidebar;` |
| `ShowNavBar: Boolean` | `Boolean` | `__property bool ShowNavBar;` |
| `NavBarBrand: string` | `string` | `__property UnicodeString NavBarBrand;` |
| `NavBarDark: Boolean` | `Boolean` | `__property bool NavBarDark;` |
| `Theme: TsgcHTMLPageTheme` | [TsgcHTMLPageTheme](../types/TsgcHTMLPageTheme.md) | `__property TsgcHTMLPageTheme * Theme;` |
| `PageTemplate: TsgcHTMLPageTemplate` | [TsgcHTMLPageTemplate](../types/TsgcHTMLPageTemplate.md) | `__property TsgcHTMLPageTemplate * PageTemplate;` |
| `PWAEnabled: Boolean` | `Boolean` | `__property bool PWAEnabled;` |
| `PWAAppName: string` | `string` | `__property UnicodeString PWAAppName;` |
| `PWAShortName: string` | `string` | `__property UnicodeString PWAShortName;` |
| `PWAThemeColor: string` | `string` | `__property UnicodeString PWAThemeColor;` |
| `PWABackgroundColor: string` | `string` | `__property UnicodeString PWABackgroundColor;` |
| `PWAIcon192: string` | `string` | `__property UnicodeString PWAIcon192;` |
| `PWAIcon512: string` | `string` | `__property UnicodeString PWAIcon512;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure RegisterComponent(aComp: TsgcHTMLComponent);
procedure UnRegisterComponent(aComp: TsgcHTMLComponent);
function GetHTML: string;
function GetSidebarHTML: string;
function GetNavBarHTML: string;
function GetSectionsHTML: string;
function GetFooterHTML: string;
function GetComponentsCSS: string;
function GetThemeCSS: string;
function GetManifestJSON: string;
function GetServiceWorkerJS: string;
procedure PreviewInBrowser;
```

C++Builder

```cpp
void __fastcall RegisterComponent(TsgcHTMLComponent * aComp);
void __fastcall UnRegisterComponent(TsgcHTMLComponent * aComp);
UnicodeString __fastcall GetHTML();
UnicodeString __fastcall GetSidebarHTML();
UnicodeString __fastcall GetNavBarHTML();
UnicodeString __fastcall GetSectionsHTML();
UnicodeString __fastcall GetFooterHTML();
UnicodeString __fastcall GetComponentsCSS();
UnicodeString __fastcall GetThemeCSS();
UnicodeString __fastcall GetManifestJSON();
UnicodeString __fastcall GetServiceWorkerJS();
void __fastcall PreviewInBrowser();
```

