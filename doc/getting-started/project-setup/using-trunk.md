# 使用 trunk

## install 
```
cargo install --locked trunk
cargo install wasm-bindgen-cli
```

## 用法

检查“[建立一个样本应用程序](https://yew.rs/docs/getting-started/build-a-sample-app)”为一个简短的指南，如何建立Yew应用程序与trunk。

你还可以通过查看我们的[示例](https://github.com/yewstack/yew/tree/master/examples)来看它的实际应用，所有的示例都是用trunk 构建的。

trunk基于作为各种类型的配置文件的index.html文件构建应用程序。与wasm-pack不同，这个工具实际上是用来创建应用程序的。
这意味着你不需要添加cdylib作为库目标。而可以使用main函数作为入口点。

要构建一个简单的yew应用程序，你只需要在项目的根目录下添加一个索引文件：
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Yew App</title>
  </head>
</html>
```

trunk CLI 提供了几个有用的命令，但是在开发过程中，`trunk service` 肯定是最有用的命令，他为你运行一个本地的服务器，并检测到变化时
自动重新构建应用程序。

当你准备好发布应用程序时，只需要运行`trunk build --release` 

这里的总结几乎没有覆盖trunk的所有特性，一定要查看[READMA](https://github.com/thedodd/trunk)!