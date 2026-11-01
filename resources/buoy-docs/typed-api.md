---
title: "plistkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: []
dependencies: []
symbols: ["ConvertPropertyList", "DecodePropertyList", "EncodePropertyList", "PropertyListsSupported"]
related: ["api.md", "getting-started.md", "index.md"]
---

# plistkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## PlistKit functions

### PropertyListsSupported

`Public Function PropertyListsSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### EncodePropertyList

`Public Function EncodePropertyList(value As JSONItem, binary As Boolean = False) As Bytes`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `value` | `JSONItem` | `ByVal` | Required |
| `binary` | `Boolean` | `ByVal` | `False` |

#### Returns

| Type |
| --- |
| `Bytes` |

### DecodePropertyList

`Public Function DecodePropertyList(data As Bytes) As JSONItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `Bytes` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `JSONItem` |

### ConvertPropertyList

`Public Function ConvertPropertyList(data As Bytes, binary As Boolean) As Bytes`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `Bytes` | `ByVal` | Required |
| `binary` | `Boolean` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Bytes` |
