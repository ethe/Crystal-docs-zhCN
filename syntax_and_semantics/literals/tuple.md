# 元祖 (Tuple)

通常采用文本方式创建 [元祖](http://crystal-lang.org/api/Tuple.html):

```crystal
tuple = {1, "hello", 'x'} # Tuple(Int32, String, Char)
tuple[0]                  #=> 1       (Int32)
tuple[1]                  #=> "hello" (String)
tuple[2]                  #=> 'x'     (Char)
```

使用 [Tuple.new](http://crystal-lang.org/api/Tuple.html#new%28%2Aargs%29-class-method) 创建一个空元祖。
