# 正则（Regex）

在 crystal 中使用 [Regex](http://crystal-lang.org/api/Regex.html) 类表示正则表达式，通常文本创建形式如下:
```crystal
foo_or_bar = /foo|bar/
heeello    = /h(e+)llo/
integer    = /\d+/
```

一个正则表达式文本使用 `/` 分割并采用 [PCRE](http://pcre.org/pcre.txt) 语法。

它可以跟这些修饰符:

* i: 忽略大小写 (PCRE_CASELESS)
* m: 多行匹配 (PCRE_MULTILINE)
* x: 扩展表达式 (PCRE_EXTENDED)

例如

```crystal
r = /foo/imx
```

斜杠必须转义:

```crystal
slash = /\//
```

提供了一个替代语法:

```crystal
r = %r(regex with slash: /)
```
