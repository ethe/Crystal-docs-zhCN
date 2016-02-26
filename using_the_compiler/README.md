# 使用编译器

当你 [安装](../installation/README.md) 好编译器后，在设置的目录下就会产生一个可执行的二进制文件。

以下将用 dollar符（`$`）指代命令行。

## 实时运行编译器

你可以简单地调用 `crystal` 接一个文件名来运行一个程序：

```
$ crystal some_program.cr
```

Crystal 文件通常使用 `.cr` 作为后缀名。

或者你也可以使用 `run` 命令：

```
$ crystal run some_program.cr
```

## 创建一个可执行文件

使用 `build` 命令来创建一个可执行文件：

```
$ crystal build some_program.cr
```

这样做将创建一个名叫 `some_program` 的文件，你可以直接执行它：

```
$ ./some_program
```

**注意：** 通过默认方式创建的文件 **没有经过完整的优化**。使用 `--release` 标记，在编译时编译器会进行完整的自动优化。

```
$ crystal build some_program.cr --release
```

请确保在生产环境以及性能测试中永远使用 `--release` 标记。

由于没有经过完整优化的编译会缩短编译时间，你可以使用 `crystal` 命令进行开发调试，这样它的载入速度让它看起来差不多就是一个解释器了。

## 创建一个应用或者库

使用 `init` 命令来创建按一个包含所有标准库的 Crystal 工程。

```
$ crystal init lib MyCoolLib
      create  MyCoolLib/.gitignore
      create  MyCoolLib/LICENSE
      create  MyCoolLib/README.md
      create  MyCoolLib/.travis.yml
      create  MyCoolLib/shard.yml
      create  MyCoolLib/src/MyCoolLib.cr
      create  MyCoolLib/src/MyCoolLib/version.cr
      create  MyCoolLib/spec/spec_helper.cr
      create  MyCoolLib/spec/MyCoolLib_spec.cr
Initialized empty Git repository in ~/MyCoolLib/.git/
```

## 其它命令与选项

不加任何参数地调用 `crystal` 可以看见完整的命令清单：

```
$ crystal
Usage: crystal [command] [switches] [program file] [--] [arguments]

Command:
    init                     generate new crystal project
    build                    compile program file
    deps                     install project dependencies
    docs                     generate documentation
    eval                     eval code from args or standard input
    run (default)            compile and run program file
    spec                     compile and run specs (in spec directory)
    tool                     run a tool
    --help, -h               show this help
    --version, -v            show version
```

使用 `--help` 标记来查看所有可用选项的帮助信息：

```
$ crystal build --help
Usage: crystal build [options] [programfile] [--] [arguments]

Options:
    --cross-compile flags            cross-compile
    -d, --debug                      Add symbolic debug info
    -D FLAG, --define FLAG           Define a compile-time flag
    --emit [asm|llvm-bc|llvm-ir|obj] Comma separated list of types of output for the compiler to emit
    -h, --help                       Show this message
    --ll                             Dump ll to .crystal directory
    --link-flags FLAGS               Additional flags to pass to the linker
    --mcpu CPU                       Target specific cpu type
    --no-color                       Disable colored output
    --no-codegen                     Don't do code generation
    -o                               Output filename
    --prelude                        Use given file as prelude
    --release                        Compile in release mode
    -s, --stats                      Enable statistics output
    --single-module                  Generate a single LLVM module
    --threads                        Maximum number of threads to use
    --target TRIPLE                  Target triple
    --verbose                        Display executed commands
```
