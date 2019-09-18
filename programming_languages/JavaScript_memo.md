## Background

Relationship between ECMAScript and JavaScript
* `ECMAScript` (or `ES`) is a scripting-language specification standarized by Ecma International in ECMA-262 and ISO/IEC 16262. It was created to standardize `JavaScript`, so as to foster mutiple independent implementations.
* best-known implementation of ECMAScript
    * [`JavaScript`](https://en.wikipedia.org/wiki/JavaScript)
    * [`JScript`](https://en.wikipedia.org/wiki/JScript)
    * [`ActionScript`](https://en.wikipedia.org/wiki/ActionScript)

## Basic Knowledges

async/await/promise
* `Promises` give us an easier way to deal with asynchrony in our code in a sequential manner, introduced in ES2015 (ES6). A promise is an asynchronous object and is used to represent either the failure or the success of any asynchronous operation
* `async`/`await` functions, a new addition with ES2017 (ES8), help us even more in allowing us to write completely synchronous-looking code while performing asynchronous tasks behind the scenes. (makes possible to write asynchronous code as if it was synchronous)

popular JavaScript engines
* [`V8`](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)), used by google chrome and node.js
* [`Rhino`](https://en.wikipedia.org/wiki/Rhino_(JavaScript_engine))
* [`SpiderMonkey`](https://en.wikipedia.org/wiki/SpiderMonkey_(JavaScript_engine)), built for firefox
* [`JavaScriptCore`](https://en.wikipedia.org/wiki/JavaScriptCore), used by safari
* [`Chakra(JScript9)`](https://en.wikipedia.org/wiki/Chakra_(JScript_engine))
* [`Chakra(JavaScript)`](https://en.wikipedia.org/wiki/Chakra_(JavaScript_engine))

for details, refer to [How JavaScript works: inside the V8 engine + 5 tips on how to write optimized code](https://blog.sessionstack.com/how-javascript-works-inside-the-v8-engine-5-tips-on-how-to-write-optimized-code-ac089e62b12e)

transpiler (like `babel`)
* source-to-source compilers, a tool that read source code written in one programming language, and produce the equivalent code in another language
* why do we need a transpiler
    * allow us to write compile-to-JavaScript languages, like CoffeeScript, TypeScript, or ClojureScript
    * let up use new and potential JavaScript features, reliably
    * contribute to the development of the ECMAScript specification

for details, refer to [JavaScript Transpilers: What They Are & Why We Need Them](https://scotch.io/tutorials/javascript-transpilers-what-they-are-why-we-need-them)

## JavaScript Engine

A engine compiles and interprets JavaScript code.

handle synchronous code
* `call stack`
    * a stack data structure, means elements can enter from the top but they can't leave if there's some element above them
    * JavaScript is single-threaded because there is a single call stack handling  the functions
* `global memory (heap)`
    * an area where js engine saves variables and function declarations
* `execution context`
    * global execution context
        * the global environment where JavaScript code runs
    * local execution context
        * for every nested function of a nested function the engine creates more local execution context (if there are inner variables or nested functions)

handle asynchronous code
* `callback queue` / `task queue`
    * every asynchronous function must pass through the callback queue before is pushed into the call stack. event loop will do these work.
* `event loop`
    * **check whether the call stack is empty**. if there's some function into the callback queue and if the call stack is free, then it's time to push the callback into the call stack
* `browser apis` / `web apis`
    * web apis are not part of the js engine but they are part of the js runtime environment which is provided by the browser. js just provides us with a mechanism to access these apis.
    * examples
        * dom apis like `document.getElementById`, `document.querySelectorAll`, `addEventListener`
        * ajax calls or `XMLHttpRequest`
        * timer functions like `setTimeout`, `setInterval`

`javascript runtime environment (jre)`
* javascript engine runs inside an environment called javascript runtime environment along with many other components. jre is responsible for making javascript asynchronous. it is the reason javascript is able to add event listeners and make http requests asynchronously.
* it is just like a container which consists of the following components
    * js engine
    * web api
    * callback queue / message queue
    * event loop
    * event table

## References
1. [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript)
2. [What is the difference between JavaScript and ECMAScript?](https://stackoverflow.com/questions/912479/what-is-the-difference-between-javascript-and-ecmascript)
3. [Equivalents in Python and JavaScript. Part 1](https://dev.to/djangotricks/equivalents-in-python-and-javascript-part-1-3317)
4. [What are JavaScript Generators and how to use them](https://codeburst.io/what-are-javascript-generators-and-how-to-use-them-c6f2713fd12e)
5. [Exploring Async/Await Functions in JavaScript](https://alligator.io/js/async-functions/)
6. [How JavaScript works: Event loop and the rise of Async programming + 5 ways to better coding with async/await](https://blog.sessionstack.com/how-javascript-works-event-loop-and-the-rise-of-async-programming-5-ways-to-better-coding-with-2f077c4438b5)
7. [JavaScript: Promises and Why Async/Await Wins the Battle](https://medium.com/better-programming/javascript-promises-and-why-async-await-wins-the-battle-4fc9d15d509f)
8. [Easy asynchrony with ES6](https://curiosity-driven.org/promises-and-generators)
9. [How does async/await work at a very low level in V8?](https://www.quora.com/How-does-async-await-work-at-a-very-low-level-in-V8)
10. [async/await native implementations](https://stackoverflow.com/questions/46908575/async-await-native-implementations)
11. [How are generators and async/await implemented in V8?](https://www.reddit.com/r/javascript/comments/44b6y9/question_how_are_generators_and_asyncawait/czpiqb9/)
12. [JavaScript Engines: How Do They Even Work? From Call Stack to Promise, (almost) Everything You Need to Know](https://www.valentinog.com/blog/engines/)
13. [JavaScript Internals: JavaScript engine, Run-time environment & setTimeout Web API](https://blog.bitsrc.io/javascript-internals-javascript-engine-run-time-environment-settimeout-web-api-eeed263b1617)
