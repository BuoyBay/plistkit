# Property lists · 0.1.0

`Import plistkit`. `PropertyListsSupported()`, `EncodePropertyList(JSONItem, binary = False)`, `DecodePropertyList(Bytes)` and `ConvertPropertyList(Bytes, binary)`. Encoding returns XML by default. Decoding returns a JSONItem and explicitly rejects plist dates/data that JSON cannot represent. Native-to-native conversion preserves all plist types. JSON null is not a valid plist value. No files or preferences are read or written implicitly.

These native operations require macOS; `PropertyListsSupported()` returns False on Windows/Linux, and unsupported operations throw rather than silently emulating an Apple API. All six compiler targets are checked; native execution is verified on macOS arm64.

Maintainers run the private validation suite before release. See the repository README for public build instructions.

Inspired by [macoslib’s Cocoa examples](https://github.com/macoslib/macoslib); implemented independently against [Apple’s API](https://developer.apple.com/documentation/foundation/propertylistserialization).
