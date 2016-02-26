# HTTP 服务器

这是一个轻盈又有趣的 HTTP 服务器的示例：

```crystal
require "http/server"

server = HTTP::Server.new(8080) do |context|
  context.response.content_type = "text/plain"
  context.response.print "Hello world! The time is #{Time.now}"
end

puts "Listening on http://0.0.0.0:8080"
server.listen
```

以上代码在你逐步阅读此文档后才能慢慢了解其中的原本，但是我们仍然可以感受到一些朦胧的印象。

* 你可以 [引入（require）](../syntax_and_semantics/requiring_files.html)在其它文件中定义的代码：

    ```ruby
    require "http/server"
    ```
* 你可以定义 [局部变量（local variables）](../syntax_and_semantics/local_variables.html)而不需要指定它的类型（尽管 Crystal 是静态类型语言）：

    ```ruby
    server = HTTP::Server.new ...
    ```

* 你的程序可以调用对象（objects）的 [方法（methods）](../syntax_and_semantics/classes_and_methods.html)（或者送入消息（sending messages））。

    ```ruby
    HTTP::Server.new(8000) ...
    ...
    Time.now
    ...
    puts "Listening on http://0.0.0.0:8080"
    ...
    server.listen
    ```

* 你可以编写代码块（code blocks）, 或者更简洁的[块（blocks）](../syntax_and_semantics/blocks_and_procs.html)，以此方便地复用代码并且使用一些函数世界中令人惊讶的特性：

    ```ruby
    HTTP::Server.new(8080) do |context|
      ...
    end
    ```

* 你可以以字符插值的方式便捷的方式嵌入你需要的字符串，语言附带了更多其它同样方便的[语法（syntax）](../syntax_and_semantics/literals.html)来创建数组（arrays）, 哈希（hashes）, 行（ranges）, 元祖（tuples）以及更多数据类型:

    ```ruby
    "Hello world! The time is #{Time.now}"
    ```
