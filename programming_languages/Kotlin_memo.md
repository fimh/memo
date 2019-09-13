## Basic Knowledges

visibility modifiers
* public - default
* private - only be visible inside the file containing the declaration
* protected - private + visible in subclass
* internal - visible within the same module
    * an IDEA module
    * a maven project
    * a gradle source set
    * a set of files compiled with one invocation of the <kotlinc> Ant task

> for details, refer to offical [Visibility Modifiers](https://kotlinlang.org/docs/reference/visibility-modifiers.html)

check the discussion on [Kotlin to support package protected visibility](https://discuss.kotlinlang.org/t/kotlin-to-support-package-protected-visibility/1544)

primary constructor/secondary constructor/init
* primary constructor - goes after the class name, allows only one
* secondary constructor - each one has to delegate to primary constructor if has
* `init` block - all property initilization and multiple init blocks will be compiled into constructor (check the decompiled kotlin bytecode)

> for details, refer to [Classes and Inheritance](https://kotlinlang.org/docs/reference/classes.html)

data class
* this kind of class will automatically generate the following
    * `equals()`/`hashCode()` pair
    * `toString()`
    * [`componentN()` functions](https://kotlinlang.org/docs/reference/multi-declarations.html)
    * [`copy()` function](https://kotlinlang.org/docs/reference/data-classes.html#copying)
* built-in [`Pair`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-pair/index.html) and [`Triple`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-triple/index.html)

> for details, refer to [Data Classes](https://kotlinlang.org/docs/reference/data-classes.html)

scope functions
* call such a function on an object with a [lambda expression](https://kotlinlang.org/docs/reference/lambdas.html)
* make your code more concise and readable
* basically, these functions do the same: execute a block of code on an object. what's different is how this object becomes available inside the block and what is the result of the whole expression (as the following table)
* recommendations on their usage
    * according to the way to refer to the context object
        * having the context object as a receiver (`this`) - for lambdas that mainly operate on the object members: call its functions or assign properties
        * having the context object as a lambda argument (`it`)
            * better when the object is mostly used as an argument in functions calls
            * better if you use multiple variables in the code block
            * you can provide a custom name for the context object inside the scope
    * according to the return value
        * context object
            * can be included into **call chains** as side steps (continue chaining function calls on the same object after them)
            * can be used in return statements of functions returning the context object

| scope function | the way to refer to the context object | return value |
| -------- | -------- | -------- |
| `with`     | `this`(as a lambda receiver)     | lambda result     |
| `run`     | `this`     | lambda result     |
| `apply`     | `this`     | context object     |
| `let`     | `it`(as a lambda argument)     | lambda result     |
| `also`     | `it`     | context object     |

> for details, refer to [Scope Functions](https://kotlinlang.org/docs/reference/scope-functions.html)

## DSA

data structures
* `Array` - represent an array in Java
    * library functions - `arrayOf()`, `arrayOfNulls()`, `intArrayOf()`/..., 
* `List`/`MutableList` - interface for immutable/mutable list
    * library functions - `listOf()`, `mutableListOf()`/`arrayListOf()` (backed by `ArrayList`)
* `Set`/`MutableSet` - interface for immutable/mutable set
    * library functions - `setOf()`, `mutableSetOf()`/`linkedSetOf()` (backed by `LinkedHashSet`), `hashSetOf()`
* `Map`/`MutableMap` - interface for immutable/mutable map (the same way as `Set`)
    * library functions - `mapOf()` `mutableMapOf()`/`linkedMapOf()` (backed by `LinkedHashMap`), `hashMapOf()`
* String
    * `String` - immutable string, just as Java
    * `StringBuilder` - mutable string, typealias `java.lang.StringBuilder`

collection data operation functions
* `map`
* `filter`
* `flatmap`
* `drop`
* `take`
* `zip`

> if you're familar with the reactivex framework, you'll find it similar  
> for details, refer to [Common operations](https://kotlinlang.org/docs/reference/collection-operations.html#common-operations)
