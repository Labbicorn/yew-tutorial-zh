# 开始 

## 项目设置 

### 概览 

你的本地开发环境将需要两个工具来编译，构建，打包和调试你的Yew应用程序。

### 安装Rust

安装Rust， 按照[官方指南](https://www.rust-lang.org/tools/instal)

> 需要注意的
> Yew 的最小支持Rust版本是1.49.0, 旧版本可能会导致意外问题，并伴随着难以理解的错误信息。你可以使用rustup show (在active toolchin下)或者rustc --version 来检查你的工具链版本。要更新工具链，请运行`rustup update`。

### 安装WebAssembly目标

Rust 可以为不同的“目标”（例如不同的处理器）编译源代码。基于浏览器的webAssembly的编译目标为`wasm32-unknown-unknown`。下面的命令将这个目标添加到开发环境中。
```
rustup target add wasm32-unknown-unknown
```

### 安装 Trunk

Trunk 是管理部署和打包的推荐工具，将在整个文档和示例中使用。有关打包和替代品的更多信息，请参见[wasm-build](https://yew.rs/docs/more/wasm-build-tools)工具。

```
# note that this might take a while to install, because it compiles everything from scratch
# Trunk also provides prebuilt binaries for a number of major package managers
# See https://trunkrs.dev/#install for further details
cargo install trunk
```

### 摘要 

现在您已经拥有了所需的所有工具，我们可以构建一个[示例应用程序](https://yew.rs/docs/getting-started/build-a-sample-app)。
