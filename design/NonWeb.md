# 非网络嵌入

尽管 WebAssembly 是为[运行在 Web 上](Web.md)设计的，它也可以在其它的环境中良好地运行。包括从用作测试的最小化 shell ，到完全的应用环境 —— 例如：在数据中心的服务器、物联网（IoT）设备或者是移动/桌面应用程序。甚至，运行嵌入在较大程序里的 WebAssembly 也是可行的。

非 Web 环境下，它可能有和 Web 环境下不同的应用编程接口（API）。[功能测试（feature testing）](FeatureTest.md)和[动态链接（dynamic linking）](DynamicLinking.md)会使其可自发现、易于使用。

非 Web 环境可能包括 JavaScript 虚拟机（例如 [node.js]）。但是，WebAssembly 也被设计为能够在没有 JavaScript 虚拟机的情况下运行。

  [node.js]: https://nodejs.org

WebAssembly 标准本身不会尝试定义任何大型可移植的类 libc 库。然而，作为 WebAssembly 语义核心、类似于原生 libc 库中的函数的某些功能，将以原始操作符（primitive operators）的身份，成为核心 WebAssembly 标准的一部分。（例如：和在许多系统中存在的 `sbrk` 函数类似的 `grow_memory` 操作符，以及未来类似于 `dlopen` 的诸操作符。）

对于在 Web 和流行的非 Web 环境之间存在重叠的地方，将会有共享的规范，但是它们会被从 WebAssembly 标准中分离出来。有一个和 JavaScript 中对应的例子 —— 仍在进行阶段（in-progress）的 [Loader](https://whatwg.github.io/loader) 规范。它因为 Web 环境和 node.js 环境被提出，并且和 JavaScript 标准存在区别。


然而，为了实现在多数情况下可期的，源码级别的可移植性。社区将会构建从源码级别的接口，映射到主机环境内置功能的库（在运行时或者构建时）。WebAssembly 将会提供原始构建块来使这些库成为可能：它们包括功能测试（feature testing）、[内建模块（builtin modules）](Modules.md#imports-and-exports)以及动态加载（dynamic loading）。两个可以预料到的早期例子是 POSIX 和 SDL。

通常，通过维持不需要 Web API 的非 Web 路径，WebAssembly 能够在许多平台上用作便携式的二进制格式，为移植性、工具和语言无关性带来巨大的好处。（因为它支持 c\c++ 级语义）
