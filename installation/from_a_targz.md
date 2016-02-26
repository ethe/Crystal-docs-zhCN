# 从 tar.gz 打包

如果你无法通过之前介绍的方式进行安装，你仍然可以尝试直接下载 Crystal 的 .tar.gz 打包文件，其中包含了所有安装需要的东西。

最新的打包文件可以在发布页面找到：GitHub: https://github.com/crystal-lang/crystal/releases

在你的平台下下载文件然后解包，其中你可以找到一个名叫 `bin/crystal` 的可执行文件。

为了让使用更方便，你可以创建一个软连接在可用的地址下：

`ln -s [full path to bin/crystal] /usr/local/bin/crystal`

然后你就可以通过简单地使用 `crystal` 命令来调用编译器。
