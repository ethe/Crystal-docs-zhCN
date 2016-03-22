# if

如果 if 条件结果为真，那么将执行对应的 `then` 分之, 如果没有匹配，将执行 `else`。

```crystal
a = 1
if a > 0
  a = 10
end
a #=> 10

b = 1
if b > 2
  b = 10
else
  b = 20
end
b #=> 20
```

如果想连写 if-else-if 的话，你可以使用 `elsif`:

```crystal
if some_condition
  do_something
elsif some_other_condition
  do_something_else
else
  do_that
end
```

执行 `if` 条件过后, 一个变量的类型取决于所有运行分之。

```crystal
a = 1
if some_condition
  a = "hello"
else
  a = true
end
# a : 字符串或布尔类型

b = 1
if some_condition
  b = "hello"
end
# b : 32位整数或字符串

if some_condition
  c = 1
else
  c = "hello"
end
# c : 32位整数或字符串

if some_condition
  d = 1
end
# d : 32位整数或Nil
```

注意，如果一个变量只在某一条件分之中声明，并且没有进入该分之，那么 `if` 条件结束之后，该变量为 `Nil` 类型。

在 `if` 条件分之里面， 变量类型由该分之的赋值语句决定，如果该分之没有进行变量赋值，类型将保持不变。

```crystal
a = 1
if some_condition
  a = "hello"
  # a : 字符串
  a.size
end
# a : 字符串或32位整数
```

因此，变量类型是由最后运行的赋值表达式决定的。

如果某一分之没有运行结束就中断, 例如 `return`, `next`, `break` 或则 `raise`, 那么在 `if` 结尾将不考虑它的类型:

```crystal
if some_condition
  e = 1
else
  e = "hello"
  # e : 字符串
  return
end
# e : 32位整数
```
