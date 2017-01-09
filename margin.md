margin 的作用

margin的auto属性会使元素的margin占满父级定位元素的空间，所以margi: 0 ,auto ，可以左右居中。margin-right:auto则会使右边距占满整行




视觉伪等高：两个并排的快级元素
可以使用
{
    padding-bottom:200px
    margin-bottom:-200px
}

相邻的非浮动元素会发生折叠，折叠发生在垂直外边距离上 即margin-top-bottom; 折叠后取最大的margin值
