# Char

一个 [字符](http://crystal-lang.org/api/Char.html) 代表了一个 [Unicode](http://en.wikipedia.org/wiki/Unicode) [码位](http://en.wikipedia.org/wiki/Code_point)。一个字符占32位。

用单引号包裹一个UTF-8字符即可创建。

```crystal
'a'
'z'
'0'
'_'
'あ'
'安'
```

你可以通过转义符（反斜杠）来表示一些特殊含义的字符：

```crystal
'\'' # single quote
'\\' # backslash
'\e' # escape
'\f' # form feed
'\n' # newline
'\r' # carriage return
'\t' # tab
'\v' # vertical tab
```

你可以使用转义符接至多三个数字来表示一个八进制码位：

```crystal
'\101' # == 'A'
'\123' # == 'S'
'\12'  # == '\n'
'\1'   # code point 1
```

你可以使用一个转义符后接*u*和四个十六进制字符来表示一个unicode码位

```crystal
'\u0041' # == 'A'
```

或者你可以用大括号包裹十六进制数来表示（0到10FFFF）

```crystal
'\u{41}'    # == 'A'
'\u{1F52E}' # == '🔮'
```
