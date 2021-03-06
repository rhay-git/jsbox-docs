> 在 JSBox 的视图系统里面，还提供了很多接口用于与用户进行交互

# $ui.pop()

可以将 push 进来的视图弹出去一层。

# $ui.popToRoot()

直接回到视图栈的第一层。

# $ui.get(id)

获得一个 view 实例，等同于 `$(id)`。

> 如果页面里面只有一个该类型的 view 则可以使用 type 获得，例如 $("list")，否则需要指定 id。

# $ui.alert(object)

给用户一个 alert 框，用于提示或者选择：

```js
$ui.alert({
  title: "Hello",
  message: "World",
  actions: [
    {
      title: "OK",
      disabled: false, // Optional
      handler: function() {

      }
    },
    {
      title: "Cancel",
      handler: function() {

      }
    }
  ]
})
```

创建一个有标题、信息和按钮的 alert，如果不提供 `actions` 的话，一个默认的确定按钮会被自动提供。

`title` 和 `message` 都是可选项，同时如果偷懒的话可以只：

```js
$ui.alert("Haha!")
```

通常可以这样来测试得到的数据，因为目前还没有提供 debug 用的组件。

# $ui.action(object)

和 `$ui.alert` 基本一样，不同的是将会采用 `action sheet` 风格提供选项，目前 iPad 上不可使用。

# $ui.menu(object)

用一种更偷懒的方式创建一个菜单：

```js
$ui.menu({
  items: ["A", "B", "C"],
  handler: function(title, idx) {

  },
  finished: function(cancelled) {
    
  }
})
```

# $ui.toast(message)

显示一个悬浮的提示信息，几秒后自动消失：

```js
$ui.toast("Hey!")
```

`toast` 也支持设置显示时间：

```js
$ui.toast("Hey!", 10)
```

此 Toast 将会显示持续 10 秒钟。

> 将 `toast` 替换成 `error` 将显示红色的 toast，通常用于显示错误信息。
> 你可以通过 $ui.clearToast() 来清除已经显示的 toast。

# $ui.loading(boolean)

在主界面显示一个正在加载的提示框：

```js
$ui.loading(true)
```

PS: 由于历史原因这个接口设计有点问题，除了使用 `true` 和 `false` 来开始或停止一个提示框以外，也可以使用是一个字符串来进行提示：

```js
$ui.loading("加载中...")
```

# $ui.progress(number)

显示加载进度，number 不处于 [0, 1] 之间时自动消失：

```js
$ui.progress(0.5)
```

同样，也支持通过一个（可选的）参数来设置提示语：

```js
$ui.progress(0.5, "下载中...")
```

# $ui.preview(object)

为文件/数据预览提供一个更便捷的方法：

```js
$ui.preview({
  title: "URL",
  url: "https://images.apple.com/v/ios/what-is/b/images/performance_large.jpg"
})
```

支持的属性：

属性 | 类型 | 说明
---|---|---
title | string | 标题
url | string | 链接
html | string | html
text | string | 文本

# $ui.create(object)

手动创建一个 view，object 参数和 $ui.render 一致：

```js
var canvas = $ui.create({
  type: "image",
  props: {
    bgcolor: $color("clear"),
    tintColor: $color("gray"),
    frame: $rect(0, 0, 100, 100)
  }
})
```

# $ui.window

获得 $ui.push 页面的 window 对象。

# $ui.controller

获得应用内最顶部的 view controller 对象。

# $ui.title

获取或设置应用内最顶部视图的标题。

# $ui.selectIcon()

从图标库中选择图标：

```js
var icon = await $ui.selectIcon();
```