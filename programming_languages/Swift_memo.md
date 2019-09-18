## DSA

* [`Array`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/Array.swift)
    * create an array using the following syntax
        * `let numbers: Array<Int> = [0, 2, 5, 3, 6]`
        * `let numbers: [Int] = [0, 2, 5, 3, 6]` - shorthand form `[Type]`
        * `let numbers = [0, 2, 5, 3, 6]` - rely on type inference
    * **mutable - assign it to a variable (`var`)**
    * **immutable - assign it to a constant (`let`)**
* [`Set`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/Set.swift)
    * create a set using the following syntax
        * `let uniNums: Set<Int> = [0, 2, 5, 3, 6]`
        * `let uniNums: Set = [0, 2, 5, 3, 6]`
    * set operations
        * `union`
        * `intersect`
        * `symmetricDifference`
        * `subtracting`
    * methods to test for equality and membership
        * `==`
        * `isSubset(of:)`
        * `isStrictSubset(of:)`
        * `isSuperset(of:)`
        * `isStrictSuperset(of:)`
        * `isDisjoint(with:)`
* [`Dictionary`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/Dictionary.swift)
    * create a dictionary (same key and value types)
        * `var numDict = Dictionary<Int, String>()`
        * `var numDict = [Int: String]()`
    * create a dictionary (different key and value types)
        * `var mixedMap: [AnyHashable: Any] = [0: "zero", 1: 1.2, "pi": 3.14]`
        * `var mixedMap = [AnyHashable(0): "Zero" as Any, AnyHashable(1): 1.0 as Any, AnyHashable("pi"): 3.14 as Any]`
* Hashable values
    * implement [`Hashable`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/Hashable.swift) protocol (and [`Equatable`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/Equatable.swift) protocol)
* [`AnyHashable`](https://github.com/apple/swift/blob/swift-5.1-branch/stdlib/public/core/AnyHashable.swift)
    * can hold a value of any type conforming to the Hashable protocol
    * can be used as the supertype for keys in heterogeneous dictionaries

> for details, refer to [Data Structures in Swift - Part 1](https://www.pluralsight.com/guides/data-structures-in-swift-part-1)

## Misc

LSP(Language Server Protocol)
* defines the protocol used between an editor/ide and a language server that provides language features like auto complete, go to definition, find all references etc
* traditionally, this work had to be repeated for each development tool, as each tool provides different apis for implementing the same feature
* lsp is to standardize the protocol for how such servers and development tools communicate. this way, a single `Language Server` can be re-used in multiple development tools, which in turn can support multiple languages within minimal effort
    * a `language server` is meant to provide the language-specific smarts and communicate with development tools over a protocol (lsp) that enables inter-process communication

> for details, refer to [Language Server Protocol](https://microsoft.github.io/language-server-protocol/)

try swift lsp with vscode
* as to enable lsp for swift, refer to [Swift Development with Visual Studio Code](https://nshipster.com/vscode/) for details
* should you come across the following issues
    * issue - `/xxx/sourcekit-lsp: error: manifest parse error(s):
<unknown>:0: error: Swift does not support the SDK 'MacOSX10.14.sdk'`
        * solution - install Xcode 11 beta and switch to it via `sudo xcode-select -s [path_to_xcode.app]`
    * issue - `Couldn't start client SourceKit Language Server (Source: Source-LSP (Extension))`
        * solution - set `Soucekit-lsp` executable explicitly in the extension settings

> for details, refer to  
> * [Swift Development with Visual Studio Code](https://nshipster.com/vscode/)
> * [Exploring the Swift standard library source code](https://useyourloaf.com/blog/exploring-the-swift-standard-library-source-code/)
> * [How to Read the Swift Standard Library Source](https://oleb.net/blog/2016/10/swift-stdlib-source/)
> * [Language Server Protocol - Swift](https://swift.gg/2019/01/15/nshipster-language-server-protocol/)
> * [Apple/sourcekit-lsp](https://github.com/apple/sourcekit-lsp/tree/swift-5.1-branch)
> * [Introducing SourceKit-LSP](https://forums.swift.org/t/introducing-sourcekit-lsp/17964)
> * [<unknown>:0: error: Swift does not support the SDK 'MacOSX10.14.sdk' #208](https://github.com/tensorflow/swift/issues/208)
> * [Xcoderelease](https://xcodereleases.com/)
> * [Switching Swift Versions inside Xcode using Toolchains](https://shashikantjagtap.net/switching-swift-versions-inside-xcode-using-toolchains/)
