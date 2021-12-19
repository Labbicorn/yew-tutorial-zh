# 使用 wasm-pack

这个工具是由`Rust/Wasm` 工作组创建的，用于构建`WebAssembly` 应用程序。
它支持将代码打包到`npm`模版，并附带一个[webpack plugin](https://github.com/wasm-tool/wasm-pack-plugin)，以方便与现有的`javascript`
应用程序即成。在[wasm-pack文档](https://rustwasm.github.io/docs/wasm-pack/introduction.html)中提供了更多信息。

> 注意⚠️
> `wasm-pack` 要求显示的设置`crate-type`以包含`cdylib`:
```
[lib]
crate-type = ["rlib", "cdylib"]
```

## 安装

```
crago install wasm-pack
```

## 构建 

这个命令将在`./pkg` 目录中使用应用程序编译的`webAssembly`一起生成一个捆绑包以及可用于启动
应用程序的`JavasScript`包装器。
```
wasm-pack build --target web
```

## Bundle

有关`rollup.js` 的更多信息，请访问本[指南](https://rollupjs.org/guide/en/#quick-start)：
```
rollup ./main.js --format iife --file ./pkg/bundle.js
```

当使用像`rollup.js`这样的`bundler`时，你可以省略 `--target web`。

## Serve

请随意使用你喜欢的服务器。在这里，我们使用一个简单的Python服务来构建应用程序。
```
python -m http.server 8000
```

如果没有安装`Python`，可以使用[simple-htttp-server](https://github.com/TheWaWaR/simple-http-server) crate来代替。