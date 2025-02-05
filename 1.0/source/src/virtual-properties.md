# Virtual properties

A virtual property is an accessor that may be used as a variable.

* A virtual property is read-only if it has only a getter.
* A virtual property is write-only if it has only a setter.
* Getter and setter are functions that belong to the virtual property.

```
function get x(): T (v);
function set x(v: T): void {}
```

Virtual properties consist of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Name*\]\] | The unqualified name of the virtual property. |
| \[\[*Type*\]\] | The type of the virtual property, inferred from the getter or setter. |
| \[\[*Visibility*\]\] | The [visibility](visibility.md) of the virtual property. |
| \[\[*ParentDefinition*\]\] | The parent definition of the virtual property. |
| \[\[*ReadOnly*\]\] | Indicates whether the virtual property is read-only or not. |
| \[\[*WriteOnly*\]\] | Indicates whether the virtual property is write-only or not. |
| \[\[*Getter*\]\] | Indicates the getter function of the virtual property. |
| \[\[*Setter*\]\] | Indicates the setter function of the virtual property. |