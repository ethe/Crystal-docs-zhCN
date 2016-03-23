# 最为后缀

`if` 可以作为表达式的后缀：

```crystal
a = 2 if some_condition

# 上述代码等价于:
if some_condition
  a = 2
end
```

使用这种方式，有时可以让代码读起来显得更自然。
