# Built-ins

`jet.lang.*` contains all global definitions of the Jet Language.

* [ ] `undefined: *`
* [ ] `Infinity`
* [ ] `NaN`
* [ ] `Object`
  * [ ] `constructor`
  * [ ] `toString()`
  * [ ] `toJSON(): *`
  * [ ] `valueOf()`
* [ ] `Class`
* [ ] JSON conventions
  * Use `Map.<*, *>` as the object data type
* [ ] `CharIterator`
  * [ ] Implements `Iterator.<Char>`
  * [ ] Includes several methods suitable for tokenizers: `remaining()`, `lookahead()`, `lookaheadSequence()`, `skip()`, `skipNumber(n)`
  * [ ] `index` property (read-only)
  * [ ] `lookbehind()`
  * [ ] `clone()`
  * [ ] Implements `Iterator`
* [ ] `Iterator.<T>` interface
  * [ ] `next(): IteratorItem.<T>`
  * [ ] `length()` optional method (consumes the iterator, returning the count as `Number`)
  * [ ] `toArray(): [T]` (consumes the iterator, returning an `Array`)
* [ ] `IteratorItem.<T>`
  * [ ] Literal class defining the properties `done: Boolean` and `value: T?`.
* [ ] Array
  * [ ] `Array` is marked final
  * [ ] All indices use the `Number` data type
  * [ ] `length` returns `Number`
  * [ ] Like Java, methods such as `indexOf()` return `-1` occasionally.
  * [ ] `getProperty()` returns `T` and throws a `RangeError` if out of bounds, instead of returning `T?`. This makes more sense for `setProperty` and `deleteProperty` as well together.
  * [ ] Methods such as `map.<T>` take a callback of two parameters (*v*, *index*).
  * [ ] `map(function(value: T, index: Number): *): [*]`
  * [ ] `reduce(function(accumulator: *, currentValue: T): *, initialValue: *): *`
    * If `initialValue` is `undefined`, take it as the first element.
* [ ] `String`
  * [ ] `length` returns a `Number` (not an integer data type) indicating the number of encoding units of the string.
  * [ ] `chars()` returns `CharIterator`
  * [ ] `apply()` formats a base string with either `[*]` or `Map.<*, *>`
    * `"$1 $$ $2".apply(["Foo", "bar"]) == "Foo $ bar"`
    * `"$x $$ $y".apply({x: "Foo", y: "bar"}) == "Foo $ bar"`
  * [ ] Add example demonstrating `"string".chars().length()` versus `"string".length` (result varies across platforms).
  * [ ] Methods such as `replace()` that accept a replacement callback function pass matches in a dedicated argument instead of passing ordinary arguments.
* [ ] Map
  * [ ] `Map` is marked final
  * [ ] `new Map(iterable: * = undefined)`
  * [ ] `proxy::keys(): Iterator.<K>`
  * [ ] `proxy::values(): Iterator.<[K, V]>`
  * [ ] `proxy::getProperty(key: K): V?`
  * [ ] `proxy::setProperty(key: K, value: V): void`
  * [ ] `proxy::deleteProperty(key: K): Boolean`
  * [ ] `entries(): Iterator.<[K, V]>`
  * [ ] `keys(): Iterator.<K>`
  * [ ] `values(): Iterator.<V>`
  * [ ] `clear()`
  * [ ] `length`
* [ ] `Set.<T>`
  * Description: setting a property to `false` is equivalent to property deletion.
  * [ ] `Set` is marked final
  * [ ] `new Set(iterable: * = undefined)`
  * [ ] `proxy::keys(): Iterator.<T>`
  * [ ] `proxy::values(): Iterator.<T>`
  * [ ] `proxy::getProperty(key: T): Boolean?`
  * [ ] `proxy::setProperty(key: T, value: Boolean): void`
  * [ ] `proxy::deleteProperty(key: T): Boolean`
  * [ ] `entries(): Iterator.<[T, Boolean]>`
  * [ ] `keys(): Iterator.<T>`
  * [ ] `values(): Iterator.<T>`
  * [ ] `clear()`
  * [ ] `length`
* [ ] XML
  * [ ] `XML` is marked final
* [ ] XMLList
  * [ ] `XMLList` is marked final

## Indices in general

In general, indices are represented by the `Number` data type in the standard objects, since it is the type that the numeric literal produces by default.