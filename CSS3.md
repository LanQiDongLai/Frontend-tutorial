### 新增长度单位

- rem 根元素字体大小的倍数
- vw 视口宽度的百分数
- vh 视口高度的百分数
- vmax 选取视口宽高较大值的百分数
- vmin 选取视口宽高较小值的百分数

### 颜色样式

`rgba`、`hsl`、`hsla`颜色，[详见](CSS-样式.md)

### 新增选择器

伪类选择器，伪元素，[详见](CSS-选择器.md)

### 盒子属性

#### 怪异盒模型

box-sizing 用于设置怪异盒模型，所谓怪异盒模型，就是指宽高设置的不再是内容区，而是边框围起来的区域（包含边框）

值可以是

- content-box（默认，按照内容区）
- border-box（按照边框范围）

#### 用户可调整大小的盒子

resize 用于设置用户可调整大小的盒子

值可以是

- horizontal（可横向拖动）
- vertical（可纵向拖动）
- both（自由拖动）
- none（不允许调整，默认）

#### 阴影

box-shadow 用于设置盒子的阴影

语法：```box-shadow: h-shadow v-shadow blur spread color inset```

```css
.container{
    /* 阴影位置偏移 */
    box-shadow: 10px 5px;
    /* 阴影位置偏移与颜色 */
    box-shadow: 10px 5px blue;
    /* 阴影位置偏移与羽化程度 */
    box-shadow：10px 5px 7px;
    /* 阴影位置偏移、羽化程度与颜色 */
    box-shadow：10px 5px 7px blue;
    /* 阴影位置偏移、羽化程度、阴影外延与颜色 */
    box-shadow：10px 5px 7px 3px blue;
    /* 阴影设置内阴影 */
    box-shadow: inset;
    /* 无阴影 */
    box-shadow: none;
}
```

> 内阴影可以将盒子想象成一个陷下去的坑，阴影就会投射到盒子内部

#### 不透明度

opacity 用于设置不透明度，值为[0,1]之间的小数

```css
.container{
    /* 设置为完全不透明 */
    opacity: 1;
    /* 设置为完全透明 */
    opacity: 0;
    /* 设置为半透明 */
    opacity: 0.5;
}
```

### 盒子背景属性

#### 背景图片原点

background-origin 用于设置背景图片原点

值可以为

- content-box 以内容区左上角为原点
- padding-box 以内边距左上角为原点
- border-box 以边框左上角为原点

#### 背景图片裁剪

background-clip 用于设置背景图片裁剪

值可以为

- content-box 内容区之外的区域裁剪
- padding-box 外边框之外的区域裁剪
- border-box 边框之外的区域裁剪（默认）
- text 文字显示之外的区域裁剪

#### 背景图片大小

background-size 用于设置背景图片大小

值可以为

- \<width\> \<height\> 使用数值来表示背景图片大小，可以用px也可以用%
- auto 原本大小
- contain 等比缩放到可以完全显示的大小
- cover 等比缩放到可以完全显示某一轴的大小

#### 复合属性

语法：```back-ground: color url repeat position / size origin clip```

> size 必须写在position后面，且用 / 分开
>
> origin clip 如果一样，可以只写一个值

#### 多背景

当需要多个背景图片显示在同一个盒子中时，可以使用逗号分隔，并为每个图片设置url，位置，重复方式

```css
.container{
    background: 
        url("../images/bg-lt") norepeat left top,
        url("../images/bg-rt") norepeat right top,
        url("../images/bg-rb") norepeat right bottom,
        url("../images/bg-lb") norepeat left bottom,
}
```

### 盒子边框属性

#### 边框圆角

border-radius 可以设置圆角半径

```css
.container{
    border-radius: 10px;
}
```

可以分开设置每个角的圆角

```css
.container{
    /* 左上角半径为10px的圆角 */
    border-top-left-radius: 10px;
    /* 左上角x半径为10px，y半径为20px的椭圆角 */
	border-top-left-radius: 10px 20px;
}
```

综合写法

```css
.container{
    border-radius: <左上角x> <右上角x> <右下角x> <左下角x> / <左上角y> <右上角y> <右下角y> <左下角y>;
}
```

#### 边框轮廓

- ```outline-width``` 外轮廓宽度

- ```outline-color``` 外轮廓颜色
- ```outline-style``` 外轮廓风格
  - `none` 无轮廓
  - `dotted` 点状轮廓
  - `dashed` 虚线轮廓
  - `solid` 实线轮廓
  - `double` 双线轮廓
- ```outline-offset``` 外轮廓与边框的距离，可以为负值

复合

```outline: <宽度> <风格> <颜色>```

> ```outline-offset```边框距离不是子属性，需要单独设置

### 新增文本属性

#### 文本阴影

text-shadow 给文本添加阴影

语法```text-shadow: <h-shadow> <v-shadow> <blur> <color>```

- `h-shadow` 必选，水平阴影位置，允许负值
- `v-shadow` 必选，垂直阴影位置，允许负值
- `blur` 可选，羽化程度（px为单位）
- `color` 可选，阴影颜色

```text-shadow: none``` 表示无阴影

#### 文本换行

white-space 设置文本换行方式

- `normal` 默认，超出边界自动换行，文本中多个换行和空格被浏览器识别为一个空格
- `pre` 原样输出，类似于`<pre>`标签
- `pre-wrap` 在`pre`基础上，超出元素边界自动换行
- `pre-line` 在`pre`基础上，换行前后的空格会被忽略
- `nowrap` 强制不换行，多个换行和空格被浏览器识别为一个空格

#### 文本溢出

text-overflow 设置文本内容溢出的呈现样式

可选值如下

- `clip` 内容溢出时，溢出部分裁切掉
- `ellipsis` 内容溢出时，文本最后为`...`

> 必须将容器的`overflow`设置为非visible值，`white-space`为nowrap值

#### 文本修饰

文本修饰原本为`text-decoration-line`,`text-decoration-style`,`text-decoration-color`三个属性，在CSS3中为`text-decoration`复合属性

[详见](./CSS-样式.md#文本修饰)

### 渐变

#### 线性渐变

#### 怪相渐变

#### 重复渐变

### 字体图标

### 二维变换

[详见](https://www.bilibili.com/video/BV1hC4y1y7Yo/)

### 三维变换

### 过渡

[详见](https://www.bilibili.com/video/BV1hC4y1y7Yo/)

### 动画

[详见](https://www.bilibili.com/video/BV1hC4y1y7Yo/)

### 多列布局

#### 容器

- `column-count` 指定列数，会自动计算列宽
- `column-width` 指定列宽，会自动计算列数
- `columns` 同时指定列宽和列数的复合属性
- `column-gap` 指定列边距
- `column-rule-style` 设置列与列之间分隔线的风格
- `column-rule-width` 设置列与列之间分隔线的宽度
- `column-rule-color` 设置列与列之间分隔线的颜色
- `column-rule` 列与列之间分隔线的复合属性

#### 子元素

`column-span` 指定是否跨列（一般用于标题）

- `none` 不跨列
- `all` 跨所有列

###  伸缩盒模型

#### 元素类型

伸缩盒模型分为两种元素：伸缩容器、伸缩项目

`display: flex` 表示该容器为伸缩容器，而其子元素都是伸缩项目

一个元素可以同时是伸缩容器、伸缩项目

无论伸缩项目原来是什么元素，伸缩项目的元素会具有块状元素的特点

#### 轴

##### 分类

- 主轴：伸缩项目沿着主轴排列，主轴默认是水平的，从左向右的
- 侧轴：与主轴垂直的就是侧轴，侧轴默认是垂直的，从上向下的

##### 主轴方向

```flex-direction```用于设置主轴方向，值可为

- `row` 从左向右
- `row-reverse` 从右向左
- `column` 从上向下
- `column-reverse` 从下向上

> 主轴方向改变之后，侧轴也改变

##### 主轴换行方式

```flex-wrap``` 用于设置主轴换行方向，值可为

- `nowrap` 默认，不换行，压缩伸缩项目的宽度
- `wrap` 自动换行
- `wrap-reverse` 向上换行

##### 主轴方向与换行的方式

`flex-flow` 复合了 `flex-direction`与`flex-wrap`两个属性，没有顺序要求

```css
.container{
    /* 主轴从左向右，换行 */
    flex-flow: row wrap;
}
```

##### 主轴对齐方式

```justify-content``` 用于设置对齐方式，值可为

- `flex-start` 主轴起点对齐，默认
- `flex-end` 主轴终点对齐
- `center` 居中对齐
- `space-around` 伸展对齐
- `space-between` 相斥对齐
- `space-evenly` 均匀分布

<img src="C:\Users\i1901\AppData\Roaming\Typora\typora-user-images\image-20240314214636139.png" alt="image-20240314214636139" style="zoom:80%;" />

##### 侧轴对齐方式

```align-items``` 用于设置侧轴对齐方式

- `flex-start` 侧轴起点对齐
- `flex-end` 侧轴终点对齐
- `center` 垂直居中对齐
- `baseline` 基线对齐
- `stretch` 拉伸（如果没有设置高）

> 多行对齐中每一行最高的元素的顶与前一行的最低的元素的底对齐，行与行之间不会出现交错的情况

##### 单独对齐

```align-self```伸缩项目属性，用于设置项目侧轴单独对齐

默认值为`auto`，表示应用伸缩容器所规定的对齐方式

##### 基准长度

```flex-basis```伸缩项目属性，用于设置主轴方向的基准长度

如果主轴横向，那么宽设置失效，如果主轴纵向，那么高设置失效

默认为`auto`表示按照宽和高的长度计算

##### 伸规则

```flex-grow``` 伸缩项目属性，用于定义伸缩项目的放大比例，默认为`0`（主轴仍存在空间，不会拉伸）

```flex-grow```的值作为权重，瓜分剩余空间

```css
/*
所有伸缩项目的权重总和为6
故container1在原来宽度基础上加上剩余空间的1/6
故container2在原来宽度基础上加上剩余空间的2/6
故container3在原来宽度基础上加上剩余空间的3/6
*/
.container1{
    flex-grow: 1;
}
.container2{
    flex-grow: 2;
}
.container3{
    flex-grow: 3;
}
```

##### 缩规则

```flex-shrink``` 伸缩项目属性，定义了项目的压缩比例，默认为1（所有伸缩项目等比例缩小）

```flex-shrink``` 的值与宽度的乘积作为权重，瓜分一整行空间

```css
/*
权重总和为1400
container1 占一行的 1/7
container2 占一行的 3/7
container3 占一行的 3/7
*/
/* 权重：200 */
.container1{
    width: 200px;
    flex-shrink: 1;
}
/* 权重：600 */
.container2{
    width: 300px;
    flex-shrink: 2;
}
/* 权重：600 */
.container3{
    width: 200px;
    flex-shrink: 3;
}
```

##### 基准长度、伸规则、缩规则复合

```flex``` 复合属性，包含```flex-grow``` ```flex-shrink``` ```flex-basis```三个属性，默认为`0 1 auto`

- 如果写```flex: 1 1 auto``` 可简写为 ```flex: auto```
- 如果写```flex: 1 1 0``` 可简写为 ```flex: 1```
- 如果写```flex: 0 0 auto``` 可简写为 ```flex: none```
- 如果写```flex: 0 1 auto``` 可简写为 ```flex:0 auto```（即默认值）

##### 项目排序

```order``` 伸缩项目属性，定义项目的排列，数值越小，越靠前，默认为`0`

### 媒体查询

#### 媒体类型

```css
/* 打印模式应用该样式，浏览模式不会应用 */
/* 浏览器可使用Ctrl+P进入打印预览 */
@media print{
    .container{
        background-color: white;
    }
}
/* 浏览模式应用该样式，打印以及其他媒体不会应用 */
@media screen{
    .container{
        background-color: violet;
    }
}
/* 所有模式均应用 */
@media all{
    .container{
        font-size: 30px;
    }
}
```

#### 媒体特性

- `width` 检测视口宽度
- `max-width` 检测视口最大宽度
- `min-width` 检测视口最小宽度
- `height` 检测视口高度
- `max-height` 检测视口最大高度
- `min-height` 检测视口最小高度
- `device-width` 检测设备屏幕宽度
- `max-device-width` 检测设备屏幕最大宽度
- `min-device-height` 检测设备屏幕最小宽度
- `orientation` 检测视口的旋转方向（是否横屏），值可为`portrait` （竖屏），`landscape`（横屏）

```css
/* 视口宽度大于700px时，背景颜色为蓝色 */
@media (min-width: 700px){
    .container{
        background-color: blue;
    }
}
```

#### 媒体选择运算符

- `and`表示且
- `or` `,` 表示或
- `not` 表示否
- `only` 表示肯定（默认，无用，用于处理IE兼容问题）

```css
/* 视口宽度大于700px时，背景颜色为蓝色 */
@media screen and (min-width: 700px){
    .container{
        background-color: blue;
    }
}
```

#### 常用响应式设计

```css
/* 超小屏幕 */
@media screen and (max-width: 768px){
}

/* 小屏幕 */
@media screen and (min-width: 768px) and (max-width: 992px){
}

/* 中等屏幕 */
@media screen and (min-width: 992) and (max-width: 1200px){
}

/* 大屏幕 */
@media screen and (min-width: 1200){
}
```

媒体选择可在外部应用时在`<link>`标签中写入

```html
<link rel="stylesheet" media="screen and (min-width: 1200)" href="../style/main.css">
```

### BFC

当元素隐藏的一部分属性，当元素具有某些特性的时候，元素布局会发生某些变化

当

- 是根元素`<html>`
- 是浮动元素
- 是绝对定位元素、固定定位元素
- 是行内块元素
- 是表格单元格：`table`、`thead`、`tbody`、`tfoot`、`th`、`td`、`tr`、`caption`
- 属性`overflow`不为`visible`块元素
- 是伸缩项目
- 是多列容器
- 属性`column-span`为`all`的元素（即使该元素没有包裹在多列容器中）
- 属性`display`的值为`flow-root`（推荐）

时

- 其子元素不会再产生margin塌陷问题
- 不会被浮动元素覆盖
- 就算子元素浮动，高度也不会塌陷
