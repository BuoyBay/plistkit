---
title: "Property lists getting started"
summary: "Install and use plistkit with an availability check and a complete example."
category: "Guides"
order: 10
keywords: ["plistkit", "install", "example"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

## Install and import

Copy the sealed `plistkit-0.1.0.buipkg` archive into your application's `packages/` folder. To build it from this repository, run `python3 tools/build_integrations.py plistkit`.

## First use

Construct a `JSONItem`, call `EncodePropertyList` for XML bytes or pass true for binary bytes, and decode JSON-compatible property lists with `DecodePropertyList`. To change only the wire format of an existing plist, use `ConvertPropertyList` instead of decoding through JSON.

```buoy
Import plistkit

Sub Main()
    If Not PropertyListsSupported() Then
        Print "Property lists require macOS."
        Return
    End If
    Dim settings As New JSONItem()
    settings.Value("name") = "Buoy"
    Dim encoded As Bytes = EncodePropertyList(settings)
    Dim restored As JSONItem = DecodePropertyList(encoded)
    Print Json.Stringify(restored)
End Sub
```

The example checks backend availability before invoking macOS-only operations. It does not catch input or access failures; catch exceptions at your application boundary and present a useful message to the user.

## Platform and error handling

macOS is required. `PropertyListsSupported()` is false on Windows and Linux, and conversion operations throw `UnsupportedOperationException` there. JSON null is not a valid plist value. Decoding rejects dates, data, or other values that JSON cannot represent; use native-to-native conversion to preserve those types. Nil input, malformed data, invalid values, and native serialization failures produce exceptions. The functions do not read files, write files, or change preferences implicitly. Returned Bytes and JSONItem values are managed by Buoy.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
