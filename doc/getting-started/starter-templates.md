# 初学者模版 

## trunk 

- [Minimal Template](https://github.com/yewstack/yew-trunk-minimal-template)，一个小的应用程序与`Trunk`建立让你开始 

## wasm-pack 

- [Minimal Template](https://github.com/yewstack/yew-wasm-pack-minimal),使用`wasm-pack`和`rollup`构建你的应用程序，和自己的服务器服务它，这里没有任何附加功能

- [webpack Template](https://github.com/yewstack/yew-wasm-pack-template)，使用`wasm-pack`和[wasm-pack-plugin](https://github.com/wasm-tool/wasm-pack-plugin)来简化webpack开发。

与其他工具不同，`wasm-pack`强制你使用`lib`,而不是`bin crate`, 并且程序的入口点带有`#[wasm_bindgen(start)]` 属性注释。

`Cargo.toml`还应该指定crate's 的类型是`cdylib`

```toml
[package]
name = "yew-app"
version = "0.1.0"
authors = ["Yew App Developer <name@example.com>"]
edition = "2018"

[lib]
# You should include "rlib" (the default crate type) otherwise your crate can't be used as a Rust library
# which, among other things, breaks unit testing
crate-type = ["rlib", "cdylib"]

[dependencies]
yew = "0.17"
wasm-bindgen = "0.2"
```

## 其他模版 

- [Paracel Template](https://github.com/dancespiele/yew-parcel-template), 由社区成员创建并使用