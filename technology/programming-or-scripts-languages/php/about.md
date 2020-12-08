# About

## PHP 8.0 - What's New and Changed?

### [Constructor Properties](https://php.watch/versions/8.0/constructor-property-promotion)

A new syntax to declare class properties right from the class constructor \(`__construct` magic method\).

```text
class User {
    public function __construct(private string $name) {}
}
```

In the constructor, PHP 8.0 supports declaring the visibility \(`public`, `private`, or `protected`\) and [type](https://php.watch/versions/7.4/typed-properties). Those properties will be registered as class properties with the same visibility and type they are declared in the constructor.

This backward-incompatible feature can help reduce boilerplate code when declaring value-object classes.

### [Union Types](https://php.watch/versions/8.0/union-types)

Union Types extend type declarations \(return types, parameters, and class properties\) to declare more than one type.

```text
function parse_value(string|int|float): string|null {}
```

It also supports `false` as a special type \(for Boolean `false`\), a trait that's prevalent in legacy code that did not use Exceptions.

### [Null-safe Operator](https://php.watch/versions/8.0/null-safe-operator)

The Null-safe operator provides safety in method/property chaining when the return value or property can be `null`.

```text
return $user->getAddress()?->getCountry()?->isoCode;
```

The `?->` null-safe operator short-circuits the rest of the expression if it encounters a `null` value, and immediately returns `null` without causing any errors.

### [`match` expressions](https://php.watch/versions/8.0/match-expression)

Match expressions are similar to `switch` blocks, but `match` blocks provide type-safe comparisons, supports a return value, does not require `break` statements to break-out, and supports multiple matching values. it also guarantees that at least one branch is matched, ensuring all cases are accounted for.

```text
$response = match('test') {
    'test' => $this->sendTestAlert(),
    'send' => $this->sendNuclearAlert(),
};
```

Not all **switch** blocks might convert well to **match** blocks. Code that requires backward-compatibility, `switch` blocks with multiple statements \(as opposed to single-line expressions\), or expects fall-through functionality still fits the **switch** statements.

### [New Functions and Classes](https://php.watch/versions/8.0#new-functions-classes)

PHP 8.0 introduces a few new functions to ease string inspections \(contains, starts with substring, or ends with substring\) to replace the meticulous `strpos() !== false` calls that are less readable, and error-prone due to weak type comparisons.

| Function | Description | Example |
| :--- | :--- | :--- |
| [`str_contains`](https://php.watch/versions/8.0/str_contains) | Haystack contains the needle somewhere | `str_contains('Foobar', 'Foo')` |
| [`str_starts_with`](https://php.watch/versions/8.0/str_starts_with-str_ends_with) | Needle _starts_ with haystack string | `str_starts_with('PHP 8.0', 'PHP)` |
| [`str_ends_with`](https://php.watch/versions/8.0/str_starts_with-str_ends_with) | Needle _ends_ with haystack string | `str_ends_with('PHP 8.0', '8.0)` |

### [New `Stringable` interface](https://php.watch/versions/8.0/stringable)

The new **Stringable** interface is automatically added to all classes that implement **\_\_toString** method, and those explicitly declare that they `implements Stringable`.

With the `Stringable` interface, it is now easy to declare types as `string|Stringable` for on functions that can accept/return strings _or_ objects with a `__toString()` method.

### [Union Types](https://php.watch/versions/8.0/union-types)

Union Types extend type declarations \(return types, parameters, and class properties\) to declare more than one type.

```text
function parse_value(string|int|float): string|null {}
```

It also supports `false` as a special type \(for Boolean `false`\), a trait that's prevalent in legacy code that did not use Exceptions.

### [New mixed pseudo type](https://php.watch/versions/8.0/mixed-type)

PHP 8.0 brings **mixed** type, that was already being widely used in DocBlock comments.

```text
function dd(mixed $var): void {
    var_dump($var);
}
```

`mixed` type can be used to indicate that it accepts any type or can return any type. In a class/interface context, `mixed` type plays by the same rules of [Liskov Substitution Principle](https://php.watch/articles/php-lsp).

### [The static return type for class methods](https://php.watch/versions/8.0/static-return-type)

**Static** return type, already supports as a DocBlock return type is now supported in PHP 8.0. The **static** return type declares an object of the called class will be returned.

```text
class Foo {
    public static function getInstance(): static {
        return new static();
    }
}
```



### [throw in expressions](https://php.watch/versions/8.0/throw-expressions)

Prior to PHP 8.0, it was not possible to **throw** exceptions from an expression \(e.g a [ternary](https://php.watch/articles/php-ternary-and-coalescing) statement\). This is now allowed in PHP 8.0.

```text
$value = isset($_GET['value'])
    ? $_GET['value']
    : throw new \InvalidArgumentException('value not set');
```

### [catch exceptions only by the type](https://php.watch/versions/8.0/catch-exception-type)

It is possible to **catch** exceptions by their type, without capturing the exception object.

```text
try {}
catch(TypeError) {
  // Did not catch the $exception object
}
```

### [Fatal errors on incompatible method signatures](https://php.watch/versions/8.0/lsp-errors)

PHP 8.0 throws fatal errors when [Liskov Substitution Principle](https://php.watch/articles/php-lsp) is not followed when classes are extended, or interfaces are implemented.

Prior to PHP 8.0, incompatible signatures only emitted a warning.

```text
class Foo {
    public function process(stdClass $item): array{}
}

class SuperFoo extends Foo{
    public function process(array $items): array{}
    //                      ^^^^^ mismatch
}
```

```text
Fatal error: Declaration of SuperFoo::process(array $items): array must be compatible with Foo::process(stdClass $item): array in ... on line ...
```

### [Class magic method signatures are strictly enforced](https://php.watch/versions/8.0/magic-method-signatures)

From PHP 8.0 and later, magic methods \(e.g `__toString()`, `__get()`, etc\), if they declare types, must implement the signature PHP expects. This is to avoid the smallest chance of the user declaring a magic method that doesn't follow the semantic meaning.

```text
class Foo {
    public function __toString(): object {
    }
}
```

Declarations like `Foo::__toString(): object` was allowed in previous PHP versions, but PHP 8.0 and throws an exception if the signature does not meet the [requirements](https://php.watch/versions/8.0/magic-method-signatures#signatures).

### [Calling non-static class methods statically result in a fatal error](https://php.watch/versions/8.0/non-static-static-call-fatal-error)

PHP 8.0 no longer allows calling class methods as a static method.

```text
class Foo {
    public function bar() {}
}
Foo::bar();
```

Previous versions emitted a deprecation notice, but from PHP 8.0 and later, this results in a fatal error.

### [Inheritance rules are not applied to `private` class methods](https://php.watch/versions/8.0/final-private-function)

PHP 8.0 relaxes the signature, `abstract`, and `static` flag enforcement for `private` class methods. This change comes from the rationale that `private` methods are just that: Private.

From PHP 8.0, it is now allowed for the child classes to declare abstract methods, and change static/flags for `private` methods.

### [`::class` magic constant is now supported on objects](https://php.watch/versions/8.0/class-constant-on-objects)

The `::class` magic constant returns the fully-qualified class name. This was only allowed on class names \(such as `Foo\Bar::class`\), but in PHP 8.0, the `::class` magic constant works on instantiated objects too.

### [+/- operators take higher precedence when used with the concat \(`.`\) operator](https://php.watch/versions/8.0/contact-add-sub-precedence)

When the mathematical + and - operators are used in the same expression with the concatenation operator \(`.`\), the + and - operators take higher precedence. This resulted in a deprecation notice in PHP versions prior to 8.0, but now it happens silently and as per the warning.

```text
echo 35 + 7 . '.' . 0 + 5;
// 42.5 in PHP >= 8.0
// 47 in PHP <= 8.0
```

