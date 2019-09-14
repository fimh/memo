### Basics

#### Reference vs. Pointer

Reference is an alias for an object - another name by which it can be called. The implemenataion is frequently identical to that of pointers. But don't think of references as pointers - a reference is the object.

A C++ reference is like a C++ pointer except for the following differences:
* You use it as if it were a value: `ref.member`, not `ptr->member`, etc. (in this sense `ref` behaves like `(*ptr)`).
* It must be initialized to point to an object - otherwise, the code won't compile.
* You can't take the address of a reference like you can with pointers (forming a pointer to a pointer).
* There's no `reference arithmetics` (but you can take the address of an object pointed by a reference and do arithmetics on it as in `&obj + 5`).

For details, refer to [References](http://yosefk.com/c++fqa/ref.html)


#### using namespace pollution

According to [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html#Namespaces), `You may not use a using-directive to make all names from a namespace available.`

```
// Do not
using namespace std;

// You can in this way - using-declaration
using std::cout;
// or, just typing std::
std::cout

```

For details, refer to
* [Why is “using namespace std;” considered bad practice?](https://stackoverflow.com/questions/1452721/why-is-using-namespace-std-considered-bad-practice)
* [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html#Namespaces)

### Compilers

#### Compilers
Clang/Clang++

> Used by xcode on macos

【TODO】
* What's difference between commands `g++`, `gcc`, `clang++` and `clang` on macos?
    * The output of help for these three commands are exactly the same with each other
    * But the execuatable program are different from each other
* What's assembly language?
* What's object code?
* What's machine code?
* What do front end and back end mean in LLVM?

GCC(g++) on linux

Microsoft Visual C++(cl) on windows

For details, refer to 
* [List of compilers](https://en.wikipedia.org/wiki/List_of_compilers#C++_compilers)
* [Compiler](https://en.wikipedia.org/wiki/Compiler#Front_end)
* [An incomplete list of C++ compilers](http://www.stroustrup.com/compilers.html)

#### Concepts

Compiler

* a computer program that translates computer code written in one programming language (the source language) into another programming language (the target language)
* is primarily used for programs that translate source code from a high-level programming language to a lower-level language (e.g., [assembly language](https://en.wikipedia.org/wiki/Assembly_language), [object code](https://en.wikipedia.org/wiki/Object_code), or [machine code](https://en.wikipedia.org/wiki/Machine_code)) to create an execuage program

LLVM

* an acronym that stands for `low level virtual machine`
* a compiling technology called the LLVM project, which is a collection of modular and resuable compiler and toolchain technologies
* can be used to develop a [`front end`](https://en.wikipedia.org/wiki/Compiler#Front_end) for any programming language and a [`back end`](https://en.wikipedia.org/wiki/Compiler#Back_end) for any instruction set architecture
* is designed around a `language-independent intermediate representation` (LLVM IR) that servers as a portable, high-level assembly language that can be optimized with a variety transformations over multiple passes

### Data Structures

all these common data structures reside in namespace `std`

#### vector

* header - `<vector>`
* equivalent in Java - `ArrayList`
* Vectors are sequence containers representing arrays that can change in size
* Internally, vectors use a dynamically allocated array to store their elements

For details, refer to [std::vector](http://www.cplusplus.com/reference/vector/vector/)

#### queue & priority_queue

* header - `<queue>`

queue
* fifo queue
* equivalent in Java - all concrete classes implement interface `Queue`
* queues are implemented as containers adaptors, which are classes that use an encapsulated object of a specific container class as its *underlying container*, providing a specific set of member functions to access its elements
* elements are **pushed** into the "back" of the specific container and **popped** from its "front"
* the standard container classes [`deque`](http://www.cplusplus.com/deque) and [`list`](http://www.cplusplus.com/list) fulfill the requirements of a queue
* by default, the standard container `deque` is used if no container class is specified

priority_queue
* priority queue
* equivalent in Java - `PriorityQueue`
* a type of container adaptor, specifically designed such that its first element is always the greatest of the elements it contains, according to some *strict weak ordering* criterion
* it is similar to a *heap*, where elements can be inserted at any moment, and only the max heap element can be retrieved (the one at the top in the *priority queue*)
* like `queue`, `priority queues` are also implemented as *container adaptors*
* elements are *poped* from the "back" of the specific container, which is known as the *top* of the priority queue
* the standard container classes [`vector`](http://www.cplusplus.com/vector) and [`deque`](http://www.cplusplus.com/deque) fulfill the requirements of a priority_queue
* by default, the standard container `vector` is used if no container class is specified

For details, refer to [std::queue](http://www.cplusplus.com/reference/queue/queue/), [std:priority_queue](http://www.cplusplus.com/reference/queue/priority_queue/)

#### set, multiset, unordered_set & unordered_multiset

set & multiset
* header - `<set>`
* set
    * equivalent in Java - `TreeSet`
    * sets are containers that store unique elements following a specific order
    * in a `set`, the value is itself the *key*, and each value must be unique
    * the elements are always const, but they can be inserted or removed from the container
    * internally, the elements in a set are always sorted following a specific strict weak ordering criterion
    * set containers are generally slower than `unorder_set` containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order
    * sets are typically implemented as `binary search trees`
* multiset
    * one key difference from `set` is: `multiset` allows multiple elements that can have equivalent values
    * no equivalent in Java, there's a similar implementation `TreeMultiSet` by [guava](https://github.com/google/guava/wiki/NewCollectionTypesExplained#multiset)

unordered_set & unordered_multiset
* header - `<unordered_set>`
* introduced in C++11
* unordered_set
    * equivalent in Java - `HashSet`
    * unordered sets are containers that store unique elements in no particular order
    * allow for fast retrieval of individual elements based on their value
    * internally, the elements are organized into `buckets` depending on their hash values to allow for fast access to individual elements directly by their values (with a constant average time complexity on average)
* unordered_multiset
    * one key difference from `unordered_set` is: `unordered_multiset` allows multiple elements that can have equivalent values
    * no equivalent in Java, there's a similar implementation `HashMultiSet` by [guava](https://github.com/google/guava/wiki/NewCollectionTypesExplained#multiset)

For details, refer to [std::set](http://www.cplusplus.com/reference/set/set/), [std::multiset](http://www.cplusplus.com/reference/set/multiset/), [std::unordered_set](http://www.cplusplus.com/reference/unordered_set/unordered_set/), [std::unordered_multiset](http://www.cplusplus.com/reference/unordered_set/unordered_multiset/)

### Reference

1. [What are the differences between a pointer variable and a reference variable in C++?](https://stackoverflow.com/questions/57483/what-are-the-differences-between-a-pointer-variable-and-a-reference-variable-in)
2. [References](http://yosefk.com/c++fqa/ref.html)
3. [An Introduction to References](https://www.embedded.com/electronics-blogs/programming-pointers/4024641/An-Introduction-to-References)
4. [Strict Weak Ordering](https://www.boost.org/sgi/stl/StrictWeakOrdering.html)
5. [set的排序条件](https://blog.csdn.net/yingxunren/article/details/3984028)
6. [MultiSet+TreeMap实现次数统计](https://blog.csdn.net/chen270310978/article/details/52945377)
7. [【C++ STL学习之五】容器set和multiset](https://blog.csdn.net/xiajun07061225/article/details/7459206)
8. [set 和 multiset 的区别](https://blog.csdn.net/weixin_35909255/article/details/70757138)
9. [STL's Red-Black Trees](http://www.drdobbs.com/cpp/stls-red-black-trees/184410531)
10. [Difference between set, multiset, unordered_set, unordered_multiset](https://www.geeksforgeeks.org/difference-set-multiset-unordered_set-unordered_multiset/)
11. [C++ STL: Policy based data structures](https://codeforces.com/blog/entry/11080)
12. [Does Java have a multiset data structure like the one in C++ STL?](https://stackoverflow.com/questions/12565587/does-java-have-a-multiset-data-structure-like-the-one-in-c-stl/20312758#20312758)
13. [Does TreeMultiset only holds the count of repeats for each key?](https://stackoverflow.com/questions/18088057/does-treemultiset-only-holds-the-count-of-repeats-for-each-key)
