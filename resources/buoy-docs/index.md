---
title: "Property lists"
summary: "Encode, decode, and convert XML and binary Apple property lists."
category: "Overview"
order: 0
keywords: ["plistkit", "macOS", "native"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Property lists

Use `plistkit` to exchange Apple property-list data in memory. The JSON-facing encoder and decoder support values representable by JSON; the native conversion function can preserve plist-only types such as dates and data.

## Platform availability

macOS is required. `PropertyListsSupported()` is false on Windows and Linux, and conversion operations throw `UnsupportedOperationException` there.

## Package use

Install `plistkit-0.1.0.buipkg` in the consumer project's `packages/` directory, then use `Import plistkit`. This package is independently sealed; it does not require importing the other desktop integration packages.

## Behavior and lifetime

JSON null is not a valid plist value. Decoding rejects dates, data, or other values that JSON cannot represent; use native-to-native conversion to preserve those types. Nil input, malformed data, invalid values, and native serialization failures produce exceptions. The functions do not read files, write files, or change preferences implicitly. Returned Bytes and JSONItem values are managed by Buoy.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
