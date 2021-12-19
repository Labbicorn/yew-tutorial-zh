# 建立一个示例应用程序


## 创建项目 
首先, 创建一个新的`crago`项目。
```shell
cargo new yew-app
```

打开新创建的目录 
```shell
cd yew-app
```

## 运行一个hello world 示例 

要验证`Rust`环境是否已经配置，请使用`cargo` 构建工具运行初始化项目。在有关构建
过程的输出之后，你应该会看到预期的`hello world`消息。
```shell
cargo run
```

## 转换成一个Yew 网络应用程序的项目 

要将这个简单的命令行应用程序转换为基本的`Yew web`应用程序，需要进行一些更改。

### 更新Update Cargo.toml 

将Yew 添加到依赖项列表中。

```toml
[package]
name = "yew-app"
version = "0.1.0"
edition = "2018"

[dependencies]
# you can check the latest version here: https://crates.io/crates/yew
yew = "0.19"
```

### 更新 main.rs

我们需要生成一个模版，该模版设置一个名为Model的根组件，该模版会在单击时显示一个更新
其值的按钮。用下面的代码替换`src/main.rs`的内容。

> 注意⚠️
> 行 `yew::start_app::<Model>()` 内部`main()`启动你的应用程序
> 并将其安装到页面`<body>`标记。如果你希望使用任何动态属性启动应用程序，可以使用
> `yew::start_app_with_props::<Model>(...)`.

```rust
use yew::prelude::*;

enum Msg {
    AddOne,
}

struct Model {
    value: i64,
}

impl Component for Model {
    type Message = Msg;
    type Properties = ();

    fn create(_ctx: &Context<Self>) -> Self {
        Self {
            value: 0,
        }
    }

    fn update(&mut self, _ctx: &Context<Self>, msg: Self::Message) -> bool {
        match msg {
            Msg::AddOne => {
                self.value += 1;
                // the value has changed so we need to
                // re-render for it to appear on the page
                true
            }
        }
    }

    fn view(&self, ctx: &Context<Self>) -> Html {
        // This gives us a component's "`Scope`" which allows us to send messages, etc to the component.
        let link = ctx.link();
        html! {
            <div>
                <button onclick={link.callback(|_| Msg::AddOne)}>{ "+1" }</button>
                <p>{ self.value }</p>
            </div>
        }
    }
}

fn main() {
    yew::start_app::<Model>();
}
```

### Create index.html

最后，在应用程序的根目录中添加一个`index.html`文件。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title> Yew App </title>
    </head>
</html>
```

### 查看你的web应用程序 

运行以下命令构建和服务应用程序
```
trunk serve
```
如果你修改了应用程序的任何文件，`trunk` 将帮助你重新构建应用程序。

## 恭喜你

你现在已经成功地设置了你的`Yew` 开发环境，并构建了你的第一个`web`应用程序。

用这个应用程序进行实验，并复习这些[例子](https://yew.rs/docs/getting-started/examples)以进一步学习。
