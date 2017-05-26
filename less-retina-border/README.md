### 使用方式一：直接使用类名
```
<div class="retina-border-all">全边框</div>
<div class="retina-border-top">上边框</div>
<div class="retina-border-tr">上-右边框</div>

```
直接在标签元素的class特性里添加类名，默认边框设置为
- 边框宽度：1px
- 边框风格：solid
- 边框颜色：#e1e1e1
- 边框圆角：0

本解决方案提供一些内置的类名以供使用，其边框类型与类名、less 函数对应关系详见下表。

边框类型 | 类名 | less 函数
---|---|---
全       边框 | retina-border-all | #retina-border-all
上       边框 | retina-border-top | #retina-border-top
右       边框 | retina-border-right | #retina-border-right
下       边框 | retina-border-bottom | #retina-border-bottom
左       边框 | retina-border-left | #retina-border-left
上-右    边框 | retina-border-tr | #retina-border-tr
上-下    边框 | retina-border-tb | #retina-border-tb
上-左    边框 | retina-border-tl | #retina-border-tl
右-下    边框 | retina-border-rb | #retina-border-rb
右-左    边框 | retina-border-rl | #retina-border-rl
下-左    边框 | retina-border-bl | #retina-border-bl

表 1：边框类型与类名、less 函数对应关系


### 使用方式二：调用 less 函数，不传入参数

某些场景下无法直接在class里添加类名，可通过在 less 里调用对应的 less 函数，这些 less 函数与内置的类名同名，只是在类名前添加 #，边框类型与 less 函数的对应关系请见表 1。

```
// 全边框函数
.border-all {
    #retina-border-all;
}

// 上边框函数
.border-top {
    #retina-border-top;
}

// 上-右边框函数
.border-tr {
    #retina-border-tr;
}
```

### 使用方式三：调用 less 函数，传递参数
```
// 调用方式一：无参数名，参数值需按序传入
.border-xxx {
    #retina-border(border-width; border-style; border-color; border-radius);
}

// 调用方式二：有参数名，参数可无序传入
.border-xxx {
    #retina-border(@borderWidth: 1px; @borderColor: red);
}
```
在详细介绍传递参数调用 less 之前，需要隆重介绍一个函数，这个函数是整个解决方案的重中之重，核心中的核心，那就是 #retina-border 函数。之所以这么说，是因为所有的内置类名、内置 less 函数都是基于 #retina-border 函数实现的，只是传入的参数不一样而已。#retina-border函数共有四个参数，依次为：边框宽度、边框风格、边框颜色、边框圆角，只要原生 css 可以实现的边框，都可以通过使用 #retina-border 函数并依次传入四个参数实现其高清屏下 1px 版本。

如下以 #retina-border 为例，介绍 less 函数的两种调用方式。

（注意，只有 #retina-border 函数是四个参数，其他基于 #retina-border 实现的函数都只有三个参数）
- 调用方式一：无参数名，参数需按序传入
    - 参数依次为：边框宽度、边框风格、边框颜色、边框圆角，参数的使用方式同原生边框，可以简写，如
        - border-width：1px 或 1px 0 或 1px 0 1px 或 1px 2px 3px 4px
    - 参数间使用分号 ; 分隔，如果想省略参数，只能从最右参数依次向左省略，不能越过省略，如
        - #retina-border(border-width); √
        - #retina-border(border-style; border-color; border-radius); ×

- 调用方式二：有参数名，参数可无序传入
    - 参数为键值对，使用 : 分开，参数间使用 ; 隔开
    - 参数的键有 @borderWidth、@borderStyle、@borderColor、@borderRadius，参数间不区分顺序


此外，不仅 #retina-border 函数可以传入参数，使用方式三中介绍的与类名同名的内置 less 函数也可以传入参数使用，函数的调用方式同 #retina-border 函数，只是参数只有三个，依次是

- @borderStyle
- @borderColor
- @borderRadius

没有 @borderWidth 参数，宽度默认为 1px。如果有任何定制需求，请调用 #retina-border 函数。
```
.border-all {
    #retina-border-all(border-style; border-color; border-radius);
}
.border-right {
    #retina-border-right(border-style; border-color; border-radius);
}
.border-tr {
    #retina-border-tr(border-style; border-color; border-radius);
}
```

### 类名及 less 函数命名方式
- 一侧边框：[. | #]retina-border-[top | right | bottom | left]
- 两侧边框：[. | #]retina-border-[tr | tb | tl | rb | rl | bl]
- 四（全）边框：[. | #]retina-border-all

其中，在两侧边框命名里，t 代表 top，r 代表 right，b 代表 bottom，l 代表 left，且 trbl 按上开始逆时针排序

## 参数配置

## 参考资料

## 版本更新

