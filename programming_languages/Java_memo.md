### Data Structures

You can find common data structures under package `java.util` and its sub-packages. 

All of these classes compose the [`Java Collections Framework`](https://en.wikipedia.org/wiki/Java_collections_framework)

#### Memo

`ArrayList` vs. `Vector`
* `ArrayList` is non-thread-safe
* `Vector` is thread-safe
* You can also get a thread-safe version of `ArrayList` via `Collections.synchronizedList(List)`

`Bag` or `multiset`
* according to `Collection`'s doc in JDK: [`Bags or multisets (unordered collections that may contain duplicate elements) should implement this interface directly.`](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)
* 【todo】What's a `bag`?
    * [Chapter 8: Bags and Sets](http://web.engr.oregonstate.edu/~sinisa/courses/OSU/CS261/CS261_Textbook/Chapter08.pdf)
    * [Multiset](https://en.m.wikipedia.org/wiki/Set_(abstract_data_type)#Multiset)
* implementation references:
    * [`Bag.java`](https://algs4.cs.princeton.edu/13stacks/Bag.java.html) from [Algorithms, 4th Edition](https://algs4.cs.princeton.edu/home/)
    * [`Bag.java`](https://github.com/apache/commons-collections/blob/master/src/main/java/org/apache/commons/collections4/Bag.java) from [apache common-collections](https://github.com/apache/commons-collections), all bag implementations reside in package [`org.apache.commons.collection4.bag`](https://github.com/apache/commons-collections/tree/master/src/main/java/org/apache/commons/collections4/bag)


【todo】
* `ArrayDeque`
    * an application - as queue storing request calls in okhttp - [`okhttp3.Dispatcher`](https://github.com/square/okhttp/blob/parent-4.2.0/okhttp/src/main/java/okhttp3/Dispatcher.kt)

data structures dedicated for android
* `ArrayMap`/`SimpleArrayMap`/`ArraySet`
* `LruCache`
* `SparseArray`/`LongSparseArray`/`SparseXXXArray`
* `Pair`
