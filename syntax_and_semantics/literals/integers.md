# 整型（Integers）

Crystal 内置有四种整数类型：[Int8](http://crystal-lang.org/api/Int8.html)，[Int16](http://crystal-lang.org/api/Int16.html)，[Int32](http://crystal-lang.org/api/Int32.html) 和 [Int64](http://crystal-lang.org/api/Int64.html)，依次代表8，16，32，64比特位数。

Crystal 内置有四中无符号整数类型：[UInt8](http://crystal-lang.org/api/UInt8.html)，[UInt16](http://crystal-lang.org/api/UInt16.html)，[UInt32](http://crystal-lang.org/api/UInt32.html) 和 [UInt64](http://crystal-lang.org/api/UInt64.html)。

一个整型文本前可以声明 `+` 或者 `-`，在文本后也可以加下划线与后缀表明其类型。如果没有显式地给出整数的类型，编译器将在`Int32`, `Int64` 和 `UInt64`中自动选择能满足定义这个整数最省需要的类型：

```crystal
1      # Int32

1_i8   # Int8
1_i16  # Int16
1_i32  # Int32
1_i64  # Int64

1_u8   # UInt8
1_u16  # UInt16
1_u32  # UInt32
1_u64  # UInt64

+10    # Int32
-20    # Int32

2147483648          # Int64
9223372036854775808 # UInt64
```

后缀之前的下划线 `_` 不是必需的，但是可以让数字变得更好读：

```crystal
1_000_000 # better than 1000000
```

二进制数以 `0b` 开头：

```crystal
0b1101 # == 13
```

八进制数以 `0o` 开头：

```crystal
0o123 # == 83
```

十六进制数以 `0x` 开头

```crystal
0xFE012D # == 16646445
0xfe012d # == 16646445
```
