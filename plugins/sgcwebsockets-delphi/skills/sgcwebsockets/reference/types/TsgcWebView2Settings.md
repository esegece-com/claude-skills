# TsgcWebView2Settings

kind: class
unit: sgcWebView2_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `ScriptEnabled: Boolean` | `Boolean` |
| `WebMessageEnabled: Boolean` | `Boolean` |
| `DefaultScriptDialogsEnabled: Boolean` | `Boolean` |
| `StatusBarEnabled: Boolean` | `Boolean` |
| `DevToolsEnabled: Boolean` | `Boolean` |
| `ContextMenuEnabled: Boolean` | `Boolean` |
| `ZoomControlEnabled: Boolean` | `Boolean` |
| `BuiltInErrorPageEnabled: Boolean` | `Boolean` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
procedure ApplyToWebView(const aSettings: ICoreWebView2Settings);
procedure ReadFromWebView(const aSettings: ICoreWebView2Settings);
```

