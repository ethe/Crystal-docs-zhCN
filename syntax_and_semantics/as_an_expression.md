# 作为表达式

`if` 的返回值就是分之最后一个表达式的返回结果:

```crystal
a = if 2 > 1
      3
    else
      4
    end
a #=> 3
```

如果 `if` 分之为空或者缺失, 默认值返回 `nil`:

```crystal
if 1 > 2
  3
end

上述代码等价于:
if 1 > 2
  3
else
  nil
end

# 另外一个例子:
if 1 > 2
else
  3
end

# 上述代码等价于:
if 1 > 2
  nil
else
  3
end
```
