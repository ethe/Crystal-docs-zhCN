# 在 Mac OSX 使用 Homebrew

通过 [Homebrew](http://brew.sh/) 可以方便地在 Mac 上安装 Crystal ：

```
brew update
brew install crystal-lang
```

如果你计划参与进项目中你也许还需要用到 LLVM 。所以将最后一行命令替换成：

```
brew install crystal-lang --with-llvm
```

## 解决在 OSX 10.11 (El Capitan) 下的问题

如果你得到一下错误信息：

```
ld: library not found for -levent
```

你需要重新安装命令行工具然后选择默认工具链：

```
$ xcode-select --install
$ xcode-select --switch /Library/Developer/CommandLineTools
```
