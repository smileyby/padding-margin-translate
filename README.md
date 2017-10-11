# 关于 padding margin translate 距离长度的相对问题

很常时间以来都不是很清楚这个`padding` `margin` `translate`所产生的距离是相对于谁的，现在就让我们一步步来搞清楚这个问题。


## margin

margin 属性为给定元素设置所有四个（上下左右）方向的外边距属性。

四个边距的属性设置可以简写。

四个外边距属性设置分别是：`margin-top` `margin-right` `margin-bottom` `margin-left`

指定的外边距允许为负数。

具体参考MDN文档：[https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)

测试代码：

```css

.box {
    width: 500px;
    height: 500px;
    background-color: #000;
}

.margins {
    width: 100px;
    height: 100px;
    font-size: 12px;
    color: #333;
    background-color: #fff;
}

.marginLeft {
    margin-left: 10%;
}

.marginRight {
    float: right;
    margin-right: 10%;
}

.marginTop {
    margin-top: 10%;
}

.marginBottom {
    margin-bottom: 10%;
}

```

```html

<div class="box">
    <div class="margins marginTop">
        margin 百分比
    </div>
</div>

```

测试结果 margin 给定距离为百分比时：

1. left/right/top/bottom 是相对于父元素的宽度的；
2. 且 `margin-top` 会做用到其父元素上

> 小贴士
> 
> [https://www.w3.org/TR/CSS21/box.html#collapsing-margins](https://www.w3.org/TR/CSS21/box.html#collapsing-margins) 根据css2.1的和模型中规定的内容（In this specification, the expression collapsing margins means that adjoining margins (no non-empty content, padding or border areas or clearance separate them) of two or more boxes (which may be next to one another or nested) combine to form a single margin.（**所有毗邻的两个或更多和元素的margin将会合并为一个margin共享。毗邻的定义：同级或嵌套的和元素，并且他们之间没有非空内容，padding或border分隔**））


> 解决办法：
> 
> 父元素或子元素使用浮动或者绝对定位absolute
> 
> 父元素 overflow:hidden
> 
> 父元素设置 padding 
> 
> 父元素设置 border

## padding

padding属性设置一个元素的内边距，padding 区域指一个元素的内容和其边界之间的空间，该属性不能为负值。[更多内容请参考 MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)

```css

.paddingLeft {
    padding-left: 10%;
}
.paddingRight {
    padding-right: 10%;
}
.paddingTop {
    padding-top: 10%;
}
.paddingBottom {
    padding-bottom: 10%;
}

```

```html 

<div class="box">
    <div class="paddings paddingLeft">
        padding 百分比
    </div>
</div>

```

测试结果：padding 给定百分比时：

1. left/right/top/bottom 是相对于父元素的宽度的

## translate

```css

.translateX {
	transform: translateX(10%);
} 

.translateY {
	transform: translateY(10%);
}

```

测试结果：translate 给定百分比

1. translateX 相对于自身宽度的百分比
2. translateY 相对于自身高度的百分比



