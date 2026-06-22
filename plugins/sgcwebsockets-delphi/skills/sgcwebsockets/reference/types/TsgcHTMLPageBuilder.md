# TsgcHTMLPageBuilder

kind: class
unit: sgcHTML_Component

## Properties

| Delphi | Type |
| --- | --- |
| `Title: string` | `string` |
| `DarkMode: Boolean` | `Boolean` |
| `IncludeBootstrap: Boolean` | `Boolean` |
| `CustomCSS: string` | `string` |
| `FooterText: string` | `string` |
| `SidebarBrand: string` | `string` |
| `SidebarWidth: string` | `string` |
| `SidebarDark: Boolean` | `Boolean` |
| `ShowSidebar: Boolean` | `Boolean` |
| `ShowNavBar: Boolean` | `Boolean` |
| `NavBarBrand: string` | `string` |
| `NavBarDark: Boolean` | `Boolean` |
| `Theme: TsgcHTMLPageTheme` | [TsgcHTMLPageTheme](./TsgcHTMLPageTheme.md) |
| `PageTemplate: TsgcHTMLPageTemplate` | [TsgcHTMLPageTemplate](./TsgcHTMLPageTemplate.md) |
| `PWAEnabled: Boolean` | `Boolean` |
| `PWAAppName: string` | `string` |
| `PWAShortName: string` | `string` |
| `PWAThemeColor: string` | `string` |
| `PWABackgroundColor: string` | `string` |
| `PWAIcon192: string` | `string` |
| `PWAIcon512: string` | `string` |
| `Version: String (read-only)` | `String` |

## Methods

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

