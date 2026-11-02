# PingOne Wallet Mobile SDK for iOS

## Overview

PingOne Wallet SDK for iOS provides the capabilities for the user to receive, save, and share credentials for identification and verification purposes. The SDK interacts with the backend services and is embedded in native iOS applications.

This repository distributes the SDK binaries via the Swift Package Manager. It contains no source code — each product is a prebuilt `xcframework`, downloaded as a zip and verified by SHA-256 checksum.

### Documentation

* PingOne Wallet SDK documentation: [docs.pingidentity.com](https://docs.pingidentity.com)
* SDK repo & sample code: [pingone-wallet-mobile-sdk-ios](https://github.com/pingidentity/pingone-wallet-mobile-sdk-ios)
* API class reference: [pingidentity.github.io/pingone-wallet-mobile-sdk-ios](https://pingidentity.github.io/pingone-wallet-mobile-sdk-ios/documentation/pingonewallet)

## Requirements

* iOS 13.0+
* Xcode 13.3+ (Swift tools version 5.6)
* Swift 5.6+

## Installation

### Swift Package Manager

1. In Xcode: **File > Add Package Dependencies…**
2. Enter the repository URL: `https://github.com/pingidentity/pingone-wallet-sdk-ios-package`
3. Set the Dependency Rule to **Exact Version** `2.0.6` (or **Up to Next Major** to receive future updates automatically).
4. Select **Add Package**, then add the products your app uses to your target.

Or in your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/pingidentity/pingone-wallet-sdk-ios-package", exact: "2.0.6")
],
targets: [
    .target(
        name: "MyApp",
        dependencies: [
            .product(name: "PingOneWallet", package: "pingone-wallet-sdk-ios-package")
        ]
    )
]
```

## Products

Most apps only need `PingOneWallet` — the other frameworks are pulled in transitively as required.

| Product | Description |
|---|---|
| `PingOneWallet` | Main SDK — credential issuance, presentation, wallet callbacks |
| `DIDSDK` | Decentralized identifiers (DID) support |
| `CryptoTools` | Cryptographic utilities |
| `AnyCoder` | JSON encode/decode helpers |
| `CommunicationManager` | Communication layer |

The package ships 9 binary frameworks in total (including support frameworks such as `JOSESwift`, `JoseTools`, `libsecp256k1`, and `secp256k1Wrapper`); Xcode embeds them automatically.

## Versions

| SDK version | Xcode dependency rule |
|---|---|
| 2.0.6 | `exact: "2.0.6"` or `from: "2.0.6"` |

Older releases remain resolvable via their tags. Never reuse a published tag — each release gets a fresh tag, zips, and checksums.

## Manual installation

Download the `xcframework.zip` files from the [releases page](https://github.com/pingidentity/pingone-wallet-sdk-ios-package/releases), unzip, and drag the frameworks into your project's **Frameworks, Libraries, and Embedded Content** (Embed & Sign). When adding manually, all 9 frameworks must be added — `DIDSDK` and `PingOneWallet` link the support frameworks at runtime.

## License

See the SDK license agreement that accompanies the PingOne Wallet SDK distribution.
