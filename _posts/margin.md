---
layout:default
title:margin的使用笔记
---
margin 的作用

margin的auto属性会使元素的margin占满父级定位元素的空间，所以margi: 0 ,auto ，可以左右居中。margin-right:auto则会使右边距占满整行


margin  百分比 
假设一个块级包含容器，宽1000px，高600px，块级子元素定义 margin:10% 5%; 大家说说 margin 的 top, right, bottom, left 计算值最终是多少？
答案是100,50，100,50
规范中注明 margin 的百分比值参照其包含块的宽度进行计算。
当然，它不会这么简单，和上篇文章 keyword auto 一样，这只发生在默认的 writing-mode: horizontal-tb; 和 direction: ltr; 的情况

当margin数值为百分比的时候 margin取值为


视觉伪等高：两个并排的快级元素
可以使用
{
    padding-bottom:200px
    margin-bottom:-200px
}

相邻的非浮动元素会发生折叠，折叠发生在垂直外边距离上 即margin-top-bottom; 折叠后取最大的margin值。



css样式优先级 

important > 内联> ID>类|伪类|属性选择>标签|伪元素>继承>通配符
   +max     >1000>100>10>1 



对于行内级置换元素来说，其高度的设置需遵循以下几点：

若宽高的计算值都为 auto 且元素有固有高度，则 height 的使用值为该固有高度；
若高度的计算值为 auto 且元素有固有高度，则 height 的使用值为该固有高度；
若高度的计算值为 auto 且宽度有 非auto 的计算值，并且元素有固有宽高比，则 height 的使用值为：宽度使用值 / 固有宽高比；
若高度的计算值为 auto 且上述条件完全不符，则 height 的使用值 不能大于150px，且宽度不能大于长方形高度的2倍。
其它类型的置换元素，其高度的定义都参照行内置换元素的定义