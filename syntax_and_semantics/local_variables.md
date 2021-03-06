# 局部变量

局部变量以小写字母开头，它们在你第一次赋值的时候就声明了。

```crystal
name = "Crystal"
age = 1
```

它们的类型与运行状态有关，并不是初始化的时候决定的。通常，它们是程序员根据代码逻辑和使用场景期望的某种类型。

例如，不同的赋值，就有不同的类型:

```crystal
flower = "Tulip"
# 此时 'flower' 是个字符串

flower = 1
# 此时 'flower' 是个 32 位整数
```

局部变量也可以使用下划线开头，但是这些名字是留给编译器的，所以一般不推荐使用（而且它们也会让代码变得丑陋，难以阅读）。
