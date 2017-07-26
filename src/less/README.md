# retina-border 之 less 版

查看此说明前，请先查看 [retina-border 的主说明文档](https://github.com/wind-stone/retina-border)


## 参数说明

retina-border 函数的参数依次为：
- borderWidth：边框宽度，默认为 1px
- borderStyle：边框类型，默认为 solid
- borderColor：边框颜色，默认为 rgba(0, 0, 0, .08)
- borderRadius：边框圆角，默认为 0

需要注意的是：
- 这些参数的值的写法跟原生 CSS 完全一致，比如 borderWidth: 1px 0 代表只有上下边框
- 如果 borderRadius 存在，会给该元素添加 border-radius 声明，且边框的 border-radius 会自动匹配 DPR

只要原生 css 可以实现的边框，都可以通过使用 retina-border 函数并依次传入四个参数实现。


## 调用

### 无参数名，参数需按序传入

```
// 无参数名，参数值需按序传入
.border-whatever {
    #retina-border(1px 2px 3px 4px; solid; red; 2px);
}
.border-whatever {
    #retina-border(1px 2px 3px 4px; solid; red);
}
.border-whatever {
    #retina-border(1px 2px 3px 4px; solid);
}
.border-whatever {
    #retina-border(1px 2px 3px 4px);
}
```

- 参数依次为：边框宽度、边框风格、边框颜色、边框圆角，各参数的使用方式同原生边框，可以简写，以 border-width 为例：
    - border-width: 1px
    - border-width: 1px 0
    - border-width: 1px 0 1px
    - border-width：1px 2px 3px 4px
- 参数间使用分号 ; 分隔，如果想省略参数，只能从最右参数依次向左省略，不能越过省略，如
    - #retina-border(border-width); √
    - #retina-border(border-style; border-color; border-radius); ×


### 有参数名，参数可无序传入

```
.border-xxx {
    #retina-border(@borderWidth: 1px; @borderColor: red);
}
```

- 参数为键值对，使用 : 分开，参数间使用 ; 隔开
- 参数的键有 @borderWidth、@borderStyle、@borderColor、@borderRadius，参数间不区分顺序
