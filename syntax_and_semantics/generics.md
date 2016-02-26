# Generics

Instance variables' types are inferred from the values assigned to them, like it was explained in [instance variables type inference](instance_variables_type_inference.html):

```crystal
class MyBox
  def initialize(@value)
  end

  def value
    @value
  end
end
```

For example, if we take the above code and add this:

```crystal
MyBox.new(1)
```

and then check what the compiler inferred with `crystal tool hierarchy file.cr`, we get:

```
+- class MyBox
       @value : Int32
```

If we create more boxes with more types:

```crystal
MyBox.new(nil)
MyBox.new("hello")
MyBox.new(1)
```

we get:

```
+- class MyBox
       @value : (Nil | String | Int32)
```

The above makes it impossible to deal with a single box of a fixed type:

```crystal
MyBox.new(1)

box = MyBox.new("hello")
box.value.size # Error: undefined method 'size' for Int32
```

In cases like this where we want each instance to have a unique type for `@value`. This is in general necessary when dealing with a collection of objects. Imagine if all arrays and hashes had their types mixed, it would be pretty annoying to deal with them.

You can make a class generic based on one or more type variables. For example:

```crystal
class MyBox(T)
  def initialize(@value)
  end

  def value
    @value
  end
end
```

Then you instantiate it like this:

```crystal
MyBox(Int32).new(1)

box = MyBox(String).new("hello")
box.value.size #=> 5
```

The above now works, because `MyBox` is now not a single type, but a family of types identified with a `T` type: `MyBox(Int32)` is a different type than `MyBox(String)`, and their `@value` variable is not shared. If we run the `tool hierarchy` command again, we get:

```
+- generic class MyBox(T)
   |
   +- generic class MyBox(String)
   |      @value : String
   |
   +- generic class MyBox(Int32)
          @value : Int32
```

However, there's a tiny flaw in the above code. This is allowed:

```crystal
MyBox(Int32).new("hello")
```

This is because there's nothing relating the `T` in the type with the instance variable `@value`. The fix is easy, we can use a [type restriction](type_restrictions.html):

```crystal
class MyBox(T)
  def initialize(@value : T)
  end

  def value
    @value
  end
end

MyBox(Int32).new(1)       # OK
MyBox(Int32).new("hello") # Error
```

The above works because when we do `MyBox(Int32)`, `T` becomes `Int32`, and when we invoke the constructor, the value passed to it must match `T`, which is `Int32`.

In a way, there's still nothing relating `T` with `@value`. However, the only way to create a `MyBox(T)` instance is by passing a `T` value, that becomes `@value`'s type, and that's what makes it all work.

But check this:

```crystal
class MyBox(T)
  def initialize(@value : T)
  end

  def value=(new_value)
    @value = new_value
  end

  def value
    @value
  end
end

box = MyBox(Int32).new(1) # OK
box.value = "hello"       # OK
```

The above is perfectly valid, because there's no type restriction in the `value=` method, and so we have just "broken" our class. Again, the solution is to use a type restriction:

```crystal
class MyBox(T)
  def initialize(@value : T)
  end

  def value=(new_value : T)
    @value = new_value
  end

  def value
    @value
  end
end

box = MyBox(Int32).new(1) # OK
box.value = "hello"       # Error
```

More than one type argument is allowed:

```crystal
class MyDictionary(K, V)
end
```

Only single letter names are allowed as names of type arguments.

## Type variables inference

Type restrictions in a generic type's constructor are free variables when type arguments were not specified, and then are used to infer them. For example:

```crystal
MyBox.new(1)       #:: MyBox(Int32)
MyBox.new("hello") #:: MyBox(String)
```

In the above code we didn't have to specify the type arguments of `MyBox`, the compiler inferred them following this process:

* `MyBox.new(value)` delegates to `initialize(@value : T)`
* `T` doesn't exist, so it's used as a free var
* Because `MyBox` is actually `MyBox(T)`, and `T` is both a free variable and a type argument, `T` becomes the type of the passed value

In this way generic types are less tedious to work with.

## Generic structs and modules

Structs and modules can be generic too. When a module is generic you include it like this:

```crystal
module Moo(T)
  def t
    T
  end
end

class Foo(U)
  include Moo(U)

  def initialize(@value : U)
  end
end

foo = Foo.new(1)
foo.t # Int32
```

Note that in the above example `T` becomes `Int32` because `Foo.new(1)` makes `U` become `Int32`, which in turn makes `T` become `Int32` via the inclusion of the generic module.

## Generic types inheritance

Generic classes and structs can be inherited. When inheriting you can specify an instance of the generic type, or delegate type variables:

```crystal
class Parent(T)
end

class Int32Child < Parent(Int32)
end

class GenericChild(T) < Parent(T)
end
```
