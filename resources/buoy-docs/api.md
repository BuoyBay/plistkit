---
title: "Property lists API"
summary: "Public plistkit types and operations with behavior and lifetime notes."
category: "Reference"
order: 20
keywords: ["plistkit", "API", "reference"]
symbols: ["PropertyListsSupported", "EncodePropertyList", "DecodePropertyList", "ConvertPropertyList"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

`Import plistkit` exposes the following public API. Properties described as read-only have no public setter.

| Symbol | Behavior |
| --- | --- |
| `PropertyListsSupported() As Boolean` | Reports whether native property-list serialization is available. |
| `EncodePropertyList(value As JSONItem, binary As Boolean = False) As Bytes` | Encode JSON-compatible values; XML is the default. |
| `DecodePropertyList(data As Bytes) As JSONItem` | Parse XML or binary plist bytes and reject values JSON cannot represent. |
| `ConvertPropertyList(data As Bytes, binary As Boolean) As Bytes` | Convert native plist data to binary when true or XML when false, preserving plist-only types. |

## Errors and availability

macOS is required. `PropertyListsSupported()` is false on Windows and Linux, and conversion operations throw `UnsupportedOperationException` there. JSON null is not a valid plist value. Decoding rejects dates, data, or other values that JSON cannot represent; use native-to-native conversion to preserve those types. Nil input, malformed data, invalid values, and native serialization failures produce exceptions. The functions do not read files, write files, or change preferences implicitly. Returned Bytes and JSONItem values are managed by Buoy.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
