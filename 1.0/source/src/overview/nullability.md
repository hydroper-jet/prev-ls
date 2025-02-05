# Nullability

The `T?` type is the primary way of working with nullable data.

* The nullish coalescing operator returns the right operand if the left operand is `null`.

```
public class ExampleClass {
    public const data: Number?;
    public function ExampleClass(data: Number?) {
        this.data = data;
    }
    public function doubleIt(): ExampleClass (
        new ExampleClass((this.data ?? 0) * 2)
    );
}
// 0
trace(new ExampleClass(null).doubleIt().data);
// 20
trace(new ExampleClass(10).doubleIt().data);
```

* The non-null operator ensures the operand is not `null`.

```
// TypeError
trace(new ExampleClass(null).data!);
```

* The optional chaining operator returns `null` if the base object is `null`.

```
public function process(a: Number?): String? (
    a?.toString(16)
);
```

## Implementation behavior

The representation of a `T?` type varies across implementations.

* A `T?` type is equivalent to a nullable reference as in ActionScript.
  * Transpilers to ActionScript may consider interning primitive values into a weak dictionary.