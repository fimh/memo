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
