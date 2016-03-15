# 多重赋值

你可以使用逗号（`,`）同时声明多个变量或者给多个变量赋值：

```crystal
name, age = "Crystal", 1

# 上述代码等同于:
temp1 = "Crystal"
temp2 = 1
name  = temp1
age   = temp2
```

注意，因为表达式赋值的时候会使用临时变量，所以变量交换可以简单的写成一行代码：

```crystal
a = 1
b = 2
a, b = b, a
a #=> 2
b #=> 1
```

如果等号右边是一个表达式，而且它的结果是下标指示器类型，那么还可以使用以下语法糖：


```crystal
name, age, source = "Crystal,1,github".split(",")

# 上述代码等同于:
temp = "Crystal,1,github".split(",")
name   = temp[0]
age    = temp[1]
source = temp[2]
```

如果等号左边只有一个变量，右边可以被视为一个数组：

```crystal
names = "John", "Peter", "Jack"

# 上述代码等同于:
names = ["John", "Peter", "Jack"]
```

多重赋值同样适用于以 `=` 结尾的方法：

```crystal
person.name, person.age = "John", 32

# 等同于:
temp1 = "John"
temp2 = 32
person.name = temp1
person.age = temp2
```

而且它同样适用于下标指示器 (`[]=`):

```crystal
objects[1], objects[2] = 3, 4

# 等同于:
temp1 = 3
temp2 = 4
objects[1] = temp1
objects[2] = temp2
```
