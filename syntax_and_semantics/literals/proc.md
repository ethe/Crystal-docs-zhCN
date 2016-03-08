# 闭包 (Proc)

[闭包](http://crystal-lang.org/api/Proc.html) 代表具有一个可选上下文(作用域数据)的函数指针。通常采用闭包文本来创建:

```crystal
# 不带参数的闭包
->{ 1 } # Proc(Int32)

# 有一个参数的闭包
->(x : Int32) { x.to_s } # Proc(Int32, String)

# 有两个参数的闭包:
->(x : Int32, y : Int32) { x + y } # Proc(Int32, Int32, Int32)
```

闭包的参数类型是必须的，直接传递到 C 绑定的库函数的闭包除外。

闭包返回类型可以自动推断。

另外也可以使用 `new` 方法创建:

```crystal
Proc(Int32, String).new { |x| x.to_s } # Proc(Int32, String)
```

这种形式允许你指定返回的类型并检查闭包调用返回结果是否与其定义类型匹配。

## Invoking

你需要使用 `call` 方法来调用闭包，调用的参数类型需要与定义参数一一对应:

```crystal
proc = ->(x : Int32, y : Int32) { x + y }
proc.call(1, 2) #=> 3
```

## From methods

闭包还可以使用已有的方法创建:

```crystal
def one
  1
end

proc = ->one
proc.call #=> 1
```

如果是有类型的参数，闭包中也应该一一对应定义:

```crystal
def plus_one(x)
  x + 1
end

proc = ->plus_one(Int32)
proc.call(41) #=> 42
```

或者是某个对象的方法:

```crystal
str = "hello"
proc = ->str.count(Char)
proc.call('e') #=> 1
proc.call('l') #=> 2
```
