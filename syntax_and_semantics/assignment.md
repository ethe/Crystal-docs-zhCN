# 赋值

Crystal 使用等号 (`=`) 赋值.

```crystal
# 局部变量赋值
local = 1

# 实例变量赋值
@instance = 2

# 类变量赋值
@@class = 3

# 全局变量赋值
$global = 4
```

上面提到的所有类型，接下来我们将一一解释。

一些包含 `=` 的语法糖也是允许的:

```crystal
local += 1  # 等于: local = local + 1

# 上面例子同样适用于以下操作符:
# +, -, *, /, %, |, &, ^, **, <<, >>

local ||= 1 # 等于: local || (local = 1)
local &&= 1 # 等于: local && (local = 1)
```

以 `=` 结尾的方法调用也拥有同样的语法糖:

```crystal
# name setter
person.name=("John")

# 等于:
person.name = "John"

# 一个索引赋值
objects.[]=(2, 3)

# 也可以写成:
objects[2] = 3

# 与赋值无关的，也具有类似语法糖:
objects.[](2, 3)

# 上面代码类似于:
objects[2, 3]
```

`=` 操作符语法糖同样适用于 setters 和 indexers。注意 `||` 和 `&&` 当使用 `[]?` 的时候会检查键是否存在。

```crystal
person.age += 1        # 等于: person.age = person.age + 1

person.name ||= "John" # 等于: person.name || (person.name = "John")
person.name &&= "John" # 等于: person.name && (person.name = "John")

objects[1] += 2        # 等于: objects[1] = objects[1] + 2

objects[1] ||= 2       # 等于: objects[1]? || (objects[1] = 2)
objects[1] &&= 2       # 等于: objects[1]? && (objects[1] = 2)
```
