# 符号 (Symbol)

[Symbol](http://crystal-lang.org/api/Symbol.html) 是一个非数字命名的常量。

```crystal
:hello
:good_bye

# 包含空格
:"symbol with spaces"

# 以问号或叹号结尾
:question?
:exclamation!

# 以及操作符
:+
:-
:*
:/
:==
:<
:<=
:>
:>=
:!
:!=
:=~
:!~
:&
:|
:^
:~
:**
:>>
:<<
:%
:[]
:[]?
:[]=
:<=>
:===
```

在 Crystal 内部，symbol 被表示成一个 `Int32` 。
