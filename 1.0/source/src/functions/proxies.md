# Proxies

A proxy is a function containing the `proxy` attribute, enclosed by a `class` or `enum` block. The name of a proxy must be one of the several proxy names listed in this section.

* [`positive`](#positive)
* [`negate`](#negate)
* [`bitwiseNot`](#bitwisenot)
* [`add`](#add)
* [`subtract`](#subtract)
* [`multiply`](#multiply)
* [`divide`](#divide)
* [`remainder`](#remainder)
* [`power`](#power)
* [`bitwiseAnd`](#bitwiseand)
* [`bitwiseXor`](#bitwisexor)
* [`bitwiseOr`](#bitwiseor)
* [`shiftLeft`](#shiftleft)
* [`shiftRight`](#shiftright)
* [`shiftRightUnsigned`](#shiftrightunsigned)
* [`to`](#to)
* [`getProperty`](#getproperty)
* [`setProperty`](#setproperty)
* [`deleteProperty`](#deleteproperty)
* [`has`](#has)
* [`keys`](#keys)
* [`values`](#values)

## positive

```
class C {
    proxy function positive(): T {}
}
```

## negate

```
class C {
    proxy function negate(): T {}
}
```

## bitwiseNot

```
class C {
    proxy function bitwiseNot(): T {}
}
```

## add

```
class C {
    proxy function add(right: C): T {}
}
```

## subtract

```
class C {
    proxy function subtract(right: C): T {}
}
```

## multiply

```
class C {
    proxy function multiply(right: C): T {}
}
```

## divide

```
class C {
    proxy function divide(right: C): T {}
}
```

## remainder

```
class C {
    proxy function remainder(right: C): T {}
}
```

## power

```
class C {
    proxy function power(right: C): T {}
}
```

## bitwiseAnd

```
class C {
    proxy function bitwiseAnd(right: C): T {}
}
```

## bitwiseXor

```
class C {
    proxy function bitwiseXor(right: C): T {}
}
```

## bitwiseOr

```
class C {
    proxy function bitwiseOr(right: C): T {}
}
```

## shiftLeft

```
class C {
    proxy function shiftLeft(right: C): T {}
}
```

## shiftRight

```
class C {
    proxy function shiftRight(right: C): T {}
}
```

## shiftRightUnsigned

```
class C {
    proxy function shiftRightUnsigned(right: C): T {}
}
```

## to

* The `to` proxy adds explicit conversion from the enclosing class to the type it returns.
* The `to` proxy may be defined multiple times.
* The `to` proxy indicates conversion failure by throwing a `TypeError` error.

```
class C {
    proxy function to(): T {}
}
```

## getProperty

```
class C {
    proxy function getProperty(k: K): T {}
}
```

## setProperty

```
class C {
    proxy function setProperty(k: K, v: V): void {}
}
```

## deleteProperty

```
class C {
    proxy function deleteProperty(k: K): Boolean {}
}
```

## has

The `has` proxy is used for the `in` operator.

```
class C {
    proxy function has(v: T): Boolean {}
}
```

## keys

The `keys` proxy is used for the `for..in` statement.

```
class C {
    proxy function keys(): Iterator.<K> {}
}
```

## values

The `values` proxy is used for the `for each` statement.

```
class C {
    proxy function values(): Iterator.<V> {}
}
```