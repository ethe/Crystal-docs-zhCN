# 编译源码

也许你想直接编译安装 Crystal 的源码，并为项目做出贡献，但是你要知道 Crystal 的编译器本身就是由 Crystal 编写的！所以首先你仍然需要用之前所述的方法安装一个 Crystal 编译器，然后再编译编译器源码。

同时你也需要提前准备好 LLVM 3.5 或者 3.6 。如果你是 Mac 用户并且安装了 Hombrew，在安装 Crystal 时加上 `--with-llvm` 标记， LLVM 会被自动配置好。

克隆以下仓库：

```
git clone https://github.com/crystal-lang/crystal.git
```

然后你就可以开始 hacking 编译器源码了 :-)

如果你想编译一个自己专属的编译器，执行 `make` 命令。这样在 `.build/crystal` 下就会编译好一个新的编译器。
请确保你已经安装[所有的依赖库](https://github.com/manastech/crystal/wiki/All-required-libraries)。阅读一下 [贡献指南](https://github.com/crystal-lang/crystal/blob/master/Contributing.md)，或许会对你有所帮助。

你也会在仓库的 `bin/crystal` 下发现一个包装好的脚本。这个脚本可以执行全局安装的编译器，也可以执行你刚刚编译好的编译器（如果存在的话）。
