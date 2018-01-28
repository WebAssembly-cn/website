# 最小可行性版本

正如在[WebAssembly 的长久目标](HighLevelGoals.md)中提到的, 我们第一个发布的目标是成为一个
最小可行性版本(Minimum Viable Product, MVP)。这里面会包含一些特性是我们在[后续发行版本:unicorn:](FutureFeatures.md)
中会逐步增加的。 最小可行性版本所包含的特性使得在当前流行浏览器和移动设备上都有与[asm.js](http://asmjs.org)大致相同的表现。

最小可行性版本的主要设计组件包含如下独立的文档：
* 在WebAssembly中，可分发、可加载和可执行的代码单元被称为模块[module](Modules.md)。

* 在模块中WebAssembly代码的行为是根据结构化堆栈机器的[指令](Semantics.md)而指定的。

* WebAssembly的二进制格式在模块的结构和代码中被规定为[二进制编码](BinaryEncoding.md),这个二进制格式被设计为由WebAssembly的实现来进行本地的解码。

* WebAssembly的文本格式被定义为类似模块的结构和代码的[文本投影](TextFormat.md)，此格式可以使用工具（例如汇编器，调试器或者性能分析器）进行读写。

* WebAssembly是设计为可以在[WEB环境](Web.md)运行以及可以在完全不同的其他环境中进行[非浏览器嵌入](NonWeb.md)的实现.
