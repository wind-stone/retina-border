# retina-border

该工具基于 stylus 编写，解决移动端 1px 物理像素边框问题。

在 DPR = 2/3 的屏幕上会显示 0.5px/0.3333333px CSS 像素，即 1px 物理像素。

注意：此方式是通过将元素的 before 伪类先放大 200%/300%，再缩小为 0.5/0.3333，元素的 before 不能再做他用，但是可以使用元素的 after 伪类。

其他版本如下：
- [less-retina-border](https://www.npmjs.com/package/less-retina-border)


## Features
- 可以模拟出 原生 CSS 的所有形式的边框，边框大小最小可以达到 1px 物理像素
- 通过 继承 功能，最终产出的代码量最少

## 文件说明

- index.styl：（解决常用需求）基于 core.styl，暴露了 上/下/左/右/全边框 的类名及函数
- core.styl：（解决定制需求）retina-border 核心函数定义声明，如果一般情况不能满足需求（比如同时需要 上下边框 或者 上下右边框），可通过直接引入 core.styl 函数，直接使用 retina-border 函数


## 使用方式

### 方式一：直接添加 类名，满足常用需求

这种方式可以满足一般需求，通过在 html 元素上添加类名，实现边框。

边框类型 | 类名
-- | --
上边框 | retina-border-top
右边框 | retina-border-right
下边框 | retina-border-bottom
左边框 | retina-border-left
全边框 | retina-border-all

引入方式
```
@import 'retina-border/index.styl'
```

使用方式
```
<div class="retina-border-all">全边框</div>
<div class="retina-border-top">上边框</div>
<div class="retina-border-tr">上-右边框</div>

```

### 方式二：调用 retina-border 核心函数，满足自定义需求

如果我们想同时添加 两条/三条 边框的类名，或者想直接调用 stylus 函数而不是添加类名，可以直接调用 retina-border 函数。

此种方式可以实现原生 CSS 的所有边框形式。

#### retina-border 参数说明

retina-border 函数的参数依次为：
- borderWidth：边框宽度，默认为 1px
- borderStyle：边框类型，默认为 solid
- borderColor：边框颜色，默认为 rgba(0, 0, 0, .08)
- borderRadius：边框圆角，默认为 0

需要注意的是：
- 这些参数的值的写法跟原生 CSS 完全一致，比如 borderWidth: 1px 0 代表只有上下边框
- 如果 borderRadius 存在，会给该元素添加 border-radius 声明，且边框的 border-radius 会自动匹配 DPR

引入方式
```
@import 'retina-border/core.styl'
```

使用方式
- 按序传参，末尾的参数可省略（省略的话会取默认值）
```
.bottom-right-border
  retina-border(0 1px 1px 0, dashed, green, 10px)

.bottom-right-border
  retina-border(0 1px 1px 0, dashed, green)

.bottom-right-border
  retina-border(0 1px 1px 0, dashed)

.bottom-right-border
  retina-border(0 1px 1px 0)
```

- 传入参数的关键字，可不按序
```
.border-all-with-radius
  retina-border(borderRadius: 50px)

.border-all-dashed
  retina-border(borderStyle: dashed)

.bottom-all-blue
  retina-border(borderColor: blue)

.top-left-border
  retina-border(borderWidth: 10px 0 0 10px)
```

## 版本更新