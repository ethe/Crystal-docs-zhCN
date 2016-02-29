# 哈希 (Hash)

[Hash](http://crystal-lang.org/api/Hash.html) 表示类型为 `K` 的键与类型为 `V` 的值的映射。最常见的创建文本是:


```crystal
{1 => 2, 3 => 4}     # Hash(Int32, Int32)
{1 => 2, 'a' => 3}   # Hash(Int32 | Char, Int32)
```

Hash 可以拥有混合类型，键、值都可以，记作 `K`/`V`。无论采用声明 `K` 和 `V` 的方式还是文本方式，哈希一旦创建成功，键和值的类型就已确定。
如果采用文本方式，其 `K` 等于创建哈希的所有键的类型集合，`V` 等于所有值的类型集合。

当创建一个空哈希的时候，你必须显示指定 `K` 和 `V`（键、值的类型）:

```crystal
{} of Int32 => Int32 # 等于 Hash(Int32, Int32).new
{}                   # 语法错误
```

## 符号类型的键

可以使用以下特定语法创建键为符号类型的哈希:

```crystal
{key1: 'a', key2: 'b'} # Hash(Symbol, Char)
```

## 字符串类型的键

可以使用以下特定语法创建键为字符串类型的哈希:

```crystal
{"key1": 'a', "key2": 'b'} # Hash(String, Char)
```

## 哈希相似类型

你可以使用哈希文本语法到其他类型里，只要此类型声明了一个带参数的 `new` 方法和 `[]=` 方法:

```crystal
MyType{"foo": "bar"}
```

如果 `MyType` 不是泛型类型, 以上代码等价于:

```crystal
tmp = MyType.new
tmp["foo"] = "bar"
tmp
```

如果 `MyType` 是泛型类型, 以上代码等价于:

```crystal
tmp = MyType(typeof("foo"), typeof("bar")).new
tmp["foo"] = "bar"
tmp
```

在这种情况下的泛型类型，参数也可以声明为:

```crystal
MyType(String, String) {"foo": "bar"}
```
