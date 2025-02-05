# Array initializer

**Syntax**

<table>
    <tr>
        <td colspan="2"><i>ArrayInitializer</i></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><b>[</b> <i>Elision</i><sub>opt</sub> <b>]</b></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><b>[</b> <i>ElementList</i> <b>]</b></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><b>[</b> <i>ElementList</i> <b>,</b> <i>Elision</i><sub>opt</sub> <b>]</b></td>
    </tr>
</table>

<table>
    <tr>
        <td colspan="2"><i>Elision</i></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><b>,</b></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><i>Elision</i> <b>,</b></td>
    </tr>
</table>

<table>
    <tr>
        <td colspan="2"><i>ElementList</i></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><i>Elision</i><sub>opt</sub> <i>AssignmentExpression</i><sup>allowIn</sup></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><i>Elision</i><sub>opt</sub> <i>InitializerRest</i></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><i>ElementList</i> <b>,</b> <i>Elision</i><sub>opt</sub> <i>AssignmentExpression</i><sup>allowIn</sup></td>
    </tr>
    <tr>
        <td>&nbsp;</td><td><i>ElementList</i> <b>,</b> <i>Elision</i><sub>opt</sub> <i>InitializerRest</i></td>
    </tr>
</table>

**Semantics**

The array initializer may be used to initialize the following types:

* `*`
* `Object`
* Tuple types
* `[T]`
* Set enumerations

Initializing `*` or `Object` results in constructing a `[*]` object.

By default, the array initializer results in an object of the `[*]` type.

Elision commas result into `undefined` elements.

```
const array = [,,,]
array.length == 3
array[0] === undefined
```

**Verification**

*ArrayInitializer*

* Let *ctxType* be the initially given context type or the `[*]` type otherwise.
* Match the nonterminal symbol with *AnyOrObject*(*ctxType*).
* Otherwise match the nonterminal symbol with *Tuple*(*ctxType*).
* Otherwise match the nonterminal symbol with *Array*(*ctxType*).
* Otherwise match the nonterminal symbol with *SetEnum*(*ctxType*).
* Otherwise throw a verify error.

*VerifyRest*(*r*, `T`) internal function

* Verifying the expression of the <i>InitializerRest</i> nonterminal symbol *r* must return a value where either whose static type includes the `values` proxy *proxy* or where whose static type is equals or a subtype of `Iterator.<T>`.
* If *proxy* is not undefined, its signature must return `Iterator.<T>` or a subtype of `Iterator.<T>`.

An element item corresponds to either an <i>Elision</i>, <i>AssignmentExpression</i><sup>allowIn</sup> or <i>InitializerRest</i>, from left-to-right.

*AnyOrObject*(*ctxType*) internal matcher

* If *ctxType* is not one of { `*`, `Object`, `Object?`, `[*]`, `[*]?` }, return match failure.
* For each element item *elem*
  * If *elem* is <i>InitializerRest</i>
    * *VerifyRest*(*elem*, `*`)
  * Else if *elem* is <i>AssignmentExpression</i><sup>allowIn</sup>
    * Verify *elem*
* Return a value of the *ctxType* type.

*Tuple*(*ctxType*) internal matcher

* If *ctxType* type is not `T` or `T?` where `T` is a tuple type, return match failure.
* For each element index *i* element item *elem*
  * If *elem* is <i>,</i>
    * Throw a verify error
  * Else if *elem* is <i>InitializerRest</i>
    * Throw a verify error
  * Else if *elem* is <i>AssignmentExpression</i><sup>allowIn</sup>
    * It is a verify error if *i* is equals or greater than the element length of `T`.
    * Limit *elem* to the *i*th element type of `T`.
* Return a value of the *ctxType* type.

When verifying *ArrayInitializer*, if the context type is `[T]` or `[T]?`:

*Array*(*ctxType*) internal matcher

* If *ctxType* type is not `[T]` or `[T]?`, return match failure.
* For each element item *elem*
  * If *elem* is <i>,</i>
    * Throw a verify error
  * Else if *elem* is <i>InitializerRest</i>
    * *VerifyRest*(*elem*, `T`)
  * Else if *elem* is <i>AssignmentExpression</i><sup>allowIn</sup>
    * Limit *elem* to `T` type.
* Return a value of the *ctxType* type.

*SetEnum*(*ctxType*) internal matcher

* If *ctxType* type is not `E` or `E?` where `E` is a set enumeration, return match failure.
* Let *c* be zero.
* Let *isConst* be true.
* For each element item *elem**
  * If *elem* is <i>,</i>
    * Throw a verify error
  * Else if *elem* is <i>InitializerRest</i>
    * Throw a verify error
  * Else if *elem* is <i>AssignmentExpression</i><sup>allowIn</sup>
    * Let *c1* be the result of limiting *elem* to the `E` type.
    * If *c1* is an `enum` constant and *isConst* is true
      * Assign *c* = bitwise OR(*c*, number of *c1*)
    * Else
      * Assign *isConst* = false
* If *isConst* is true
  * Return an `enum` constant with number *c* and static type as *ctxType*.
* Return a value of the *ctxType* type.