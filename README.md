# retina-border

实现移动端 1px 物理像素边框，可实现任意原生的边框，包含 less、stylus 版本

在 DPR = 2 的屏幕上会显示 0.5px CSS 像素，即 1px 物理像素。

在 DPR = 3 的屏幕上会显示 0.3333333px CSS 像素，即 1px 物理像素。


注意：

此方式是通过将元素的 before 伪类来实现 1px 物理像素边框的，因此元素的 before 不能再做他用，但是可以使用元素的 after 伪类。


## Features
- 可以模拟出 原生 CSS 的所有形式的边框，边框大小最小可以达到 1px 物理像素
- 通过 继承 功能，最终产出的代码量最少


## 安装

### NPM

```
npm install retina-border -S
```

通过 webpack 使用（需要结合 less-loader/stylus-loader）
```
// less
@import '~retina-border/src/less/index.less';

// stylus
@import '~retina-border/src/stylus/index.styl'
```


### 直接下载

- [less 版](https://github.com/wind-stone/retina-border/tree/master/src/less)
- [stylus 版](https://github.com/wind-stone/retina-border/tree/master/src/stylus)

文件说明

- index.less/styl：（满足常用需求）引入 core.less/styl，暴露了 上/下/左/右/全边框 的类名
- core.less/styl：（满足定制需求）retina-border 核心函数定义声明，如果有定制需求（比如同时需要 上下边框 或者 上下右边框），可跳过引入 index.less/stylus 直接引入 core.less/styl 函数，进入使用 retina-border 函数


## 使用

本工具提供一些常用的边框类型以供使用，其边框类型与类名（以及 less/stylus 函数）对应关系详见下表。
边框类型 | 类名 | less 函数 | stylus
---|---|---|---
全 边框 | retina-border-all | #retina-border-all | retina-border-all
上 边框 | retina-border-top | #retina-border-top | retina-border-top
右 边框 | retina-border-right | #retina-border-right | retina-border-right
下 边框 | retina-border-bottom | #retina-border-bottom | retina-border-bottom
左 边框 | retina-border-left | #retina-border-left | retina-border-left


### 通用方式：直接添加 类名，满足常用需求

这种方式可以满足一般需求，通过在 html 元素上添加类名，实现边框。

```
<div class="retina-border-all">全边框</div>
<div class="retina-border-top">上边框</div>
<div class="retina-border-right">右边框</div>
<div class="retina-border-bottom">下边框</div>
<div class="retina-border-left">左边框</div>
```

边框的默认设置为
- 边框宽度 border-width：1px
- 边框风格 border-style：solid
- 边框颜色 border-color：#e1e1e1
- 边框圆角 border-radius：0


### 调用 retina-border 核心函数，满足定制需求

- 某些场景下无法直接在 class 里添加类名，需要在（预处理）样式文件里添加边框
- 有其他边框需求，如想添加两条/三条边框，需要不同的 border-width/style/color等

如果遇到如下需求，可以直接调用 retina-border 函数，此种方式可以实现原生 CSS 的所有边框形式。

具体请参考：

- [less](https://github.com/wind-stone/retina-border/tree/master/src/less)
- [stylus](https://github.com/wind-stone/retina-border/tree/master/src/stylus)