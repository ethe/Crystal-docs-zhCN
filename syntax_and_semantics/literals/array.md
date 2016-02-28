# 数组 (Array)

[Array](http://crystal-lang.org/api/Array.html) 是一个泛型类型，包含的元素类型为 `T`。 一般采用数组标识符来创建数组:

```crystal
[1, 2, 3]         # Array(Int32)
[1, "hello", 'x'] # Array(Int32 | String | Char)
```

一个数组可以拥有混合类型 `T`，及不同类型的集合, 无论是显示的指定类型为 `T` 还是使用数组标识符，数组一旦创建其类型就已经确定。 如果使用数组标识符创建, 数组的类型 `T` 就是其所有元素的类型集合。

当创建一个空数组的时候，必须指定为类型 `T`:

```crystal
[] of Int32 # 与 Array(Int32).new 等同
[]          # 语法错误
```

## 字符串数组

字符串数组可以使用特殊的语法创建:

```crystal
%w(one two three) # ["one", "two", "three"]
```

## 符号数组

符号数组可以使用特殊的语法创建:

```crystal
%i(one two three) # [:one, :two, :three]
```

## 类似数组类型

你可以在其他类型中使用这种特殊数组标识符语法，只要此类型定义了带有参数的 `new` 方法 和 `<<` 方法:

```crystal
MyType{1, 2, 3}
```

如果 `MyType` 不是通用的, 以上代码相当于:

```crystal
tmp = MyType.new
tmp << 1
tmp << 2
tmp << 3
tmp
```

如果 `MyType` 是通用的, 以上代码相当于:

```crystal
tmp = MyType(typeof(1, 2, 3)).new
tmp << 1
tmp << 2
tmp << 3
tmp
```

这种情况下的通用类型, 参数也可以声明为:

```crystal
MyType(Int32 | String) {1, 2, "foo"}
```
