# Scopes

A scope consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*ParentScope*\]\] | The parent scope. |
| \[\[*Properties*\]\] | Properties of the scope as a dictionary of string to symbol. |
| \[\[*Imports*\]\] | Set of package imported properties. |
| \[\[*OpenPackages*\]\] | Set of open packages. |
| \[\[*PackageAliases*\]\] | Set of package aliases. |
| \[\[*LocalVariableScopeCount*\]\] | Number of local variable scopes. Used for variable shadowing. |

The \[\[*Imports*\]\] property of a scope holds *non aliased* properties imported from a package.

The \[\[*OpenPackages*\]\] property of a scope holds *non aliased* opened packages.

The \[\[*PackageAliases*\]\] property of a scope contains package aliases resulting from the `import` directive.

An `import` directive that aliases a property or package contributes an alias to \[\[*Properties*\]\].

## With scope

A `with` scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Object*\]\] | The object specified in the `with` statement. |

## Filter operator scope

A filter operator scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Base*\]\] | The base object of the filter operator. |

## Activation scope

An activation scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Function*\]\] | The function to which this scope belongs. |
| \[\[*This*\]\] | The object returned by the `this` literal. |

## Class scope

A `class` scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Class*\]\] | The enclosing class. |

## Enum scope

A `enum` scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Class*\]\] | The enclosing `enum`. |

## Interface scope

An `interface` scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Interface*\]\] | The enclosing `interface`. |

## Package scope

A `package` scope in addition consists of the following internal properties:

| Internal property | Description |
| ----------------- | ----------- |
| \[\[*Package*\]\] | The enclosing `package`. |