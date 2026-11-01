# Read and write XML and binary property lists

`Import plistkit`. `PropertyListsSupported()`, `EncodePropertyList(JSONItem, binary = False)`, `DecodePropertyList(Bytes)` and `ConvertPropertyList(Bytes, binary)`. Encoding returns XML by default. Decoding returns a JSONItem and explicitly rejects plist dates/data that JSON cannot represent. Native-to-native conversion preserves all plist types. JSON null is not a valid plist value. No files or preferences are read or written implicitly.

These native operations require macOS; `PropertyListsSupported()` returns False on Windows/Linux, and unsupported operations throw rather than silently emulating an Apple API. All six compiler targets are checked; native execution is verified on macOS arm64.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add plistkit --git https://github.com/BuoyBay/plistkit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer plistkit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

The generated agent files and editor settings stay local and are ignored by Git.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
