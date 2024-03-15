## 颜色

```css
span{
    /* 用名称来表示颜色 */
    background-color: skyblue;
    /* 用rgb来表示颜色*/
    background-color: rgb(138,43,226);
    background-color: rgb(73%,10%,92%);
    /* 用rgba来表示颜色和透明度 */
    background-color: rgba(138,43,226,0.8);
    background-color: rgba(73%,10%,92%,80%);
    /* 用#RRGGBB或者#RRGGBBAA十六进制来表示 */
    background-color: #a310f8;
    background-color: #f3a; /* 表示#ff33aa */
    /* 用hsl（色相，饱和度，亮度）或hsla来表示颜色 */
    background-color: hsl(12deg,100%,50%);
    background-color: hsl(12deg,100%,50%,100%);
}
```

## 长度单位

- px 像素
- em 相对元素font-size的倍数
- rem 相对根元素(html)font-size大小的倍数
- % 相对父元素进行计算

## 字体

### 基本常识

- 衬线字体（一般用于印刷，字体特点为中文横竖撇捺，以及英文字母的每一个笔画的开头和末尾都有特殊的装饰）
- 非衬线字体（更倾向于手写体，或者某些花体）

字体设计框，字体大小指的是字体设计框的大小，但是字体的渲染范围是比字体设计框要大的，字体中的某个字可以超过字体设计框的大小，例如字母g，他的下沿超过了字体设计框

基线，不同大小的文本对齐方式一般是基线对齐，字体一般按照字母x显示的下沿作为基线

字体下沉，一般字体中英文字母都会渲染在字体设计框中间偏下的位置，但这不是绝对的

### 字体大小

使用 font-size 设置文本大小

```font-size: 18px```

> 不同的浏览器的字体默认大小不同
>
> 当字体大小小于浏览器最小字号的时候，浏览器会限制在最小字号
>
> 当字体大小为0时，文字不显示不占位
>
> 字体大小样式可继承

### 字体族

使用 font-family 设置文本字体

```font-family: "STCaiyun", "STHupo"```

> 中文名称也行，但英文名称兼容性更好
>
> 当名称中存在空格时，必须使用双引号
>
> 当所用字在先写的字体中找不到时，才会向后找字体

### 字体风格

使用 font-style 设置文本风格

```font-family: normal``` 无风格

```font-family: italic``` 字体斜体（推荐 当字体不自带斜体时自动强制斜体）

```font-famliy: oblique``` 强制斜体

### 字体粗细

使用 font-weight 设置文本粗细

```font-weight: lighter``` 细

```font-weight: normal``` 正常

```font-weight: bold``` 粗

```font-weight: bolder``` 更粗（多数字体不支持）

### 复合

```font: [其他属性（风格，粗细）] 字体大小 字体族```

```css
.text{
    font: bold italic 24px "STCaiyun","STHupo"
}
```

## 文本

### 文本颜色

```color ``` 设置文本颜色，属性值[详见](#颜色)

### 文本间距

`letter-spacing` 字母间距

`word-spacing` 单词间距（空格作为划分单词的依据）

> 属性值以px为单位，可为负值（重叠）

### 文本修饰

`text-decoration` 用来修饰文本

`text-decoration: none` 无修饰

`text-decoration: underline` 下划线

`text-decoration: overline` 上划线

`text-decoration: line-through` 删除线

其他配合修饰（不可单独使用）

`text-decoration: dotted` 虚线

`text-decoration: wavy` 波浪线

`text-decoration: red` 红线

```css
.text{
    /* 红色波浪下划线 */
    text-decoration: red wavy underline;
}
```

### 文本缩进

text-indent 设置文本缩进

```css
.text{
    /* 文本缩进两字符大小 */
    text-indent: 2em
}
```

### 文本对齐

text-align 用于设置文本对齐

`text-align: left` 左对齐

`text-align: center` 居中对齐

`text-align: right` 右对齐

### 文本行高

`line-height` 用于设置行高

```css
.text{
    /* 以像素确定行高 */
    line-height: 40px;
    /* 以字体倍率确定行高 */
    line-height: 1.5;
    /* 以百分比确定行高 */
    line-height: 150%;
    /* 以浏览器默认确定行高 */
    line-height: normal;
}
```

> 行高为0时，所有行会重叠
>
> 行高样式是可继承的

### 文本垂直对齐

vertical-align 用于同一行元素的对齐方式

`vertical-align: baseline` 该元素基线与父元素基线对齐（默认）

`vertical-align: top` 该元素顶部与父元素顶部对齐

`vertical-align: middle` 该元素中间与父元素的字母x中心点所在位置对齐

`vertical-align: bottom` 该元素底部与父元素底部对齐

#### 技巧：文本垂直对齐

使父元素的`height`等于`line-height`即可

## 列表

### 列表符号

list-style-type 用于设置列表符号

`list-style-type: none` 不显示

`list-style-type: square` 实心方块

`list-style-type: disc` 圆形

`list-style-type: decimal` 数字

`list-style-type: lower-roman` 小写罗马字

`list-style-type: upper-roman` 大写罗马字

`list-style-type: lower-alpha` 小写字母

`list-style-type: upper-alpha` 大写字母

### 列表符号位置

list-style-position 用于设置列表符号位置

`list-style-position: inside` 符号在`li`里面

`list-style-position: outside` 符号在`li`外面

### 自定义列表符号（图片）

list-style-image 用于自定义列表符号

`list-style-image: url(...)` 设置列表符号图片

### 复合

`list-style` 上述属性的复合，无顺序和数量要求

## 边框

> 可用于表格样式

`border-width` 边框宽度

`border-color` 边框颜色

`border-style` 边框风格

- `border-style: none` 无样式
- `border-style: solid` 实线
- `border-style: dashed` 虚线
- `border-style: dotted` 点线
- `border-style: double` 双实线

`border` 复合，无顺序数量要求

## 表格

### 列宽度布局

table-layout 可用于设置列宽度布局

`table-layout: auto` 按照内容设置列宽

`table-layout: fixed` 每个列宽都一致

### 单元格边框是否合并

`border-collapse` 用于设置是否合并边框

``

### 单元格间距

`border-spacing` 用于设置单元格间距，当边框合并时不生效

```css
.text{
    border-spacing: 5px;
}
```

### 单元是否显示

empty-cells 用于设置单元是否显示

`empty-cells: show` 显示

`empty-cells: hidden` 隐藏

### 标题位置

caption-side 用于设置表格标题位置

`caption-side: top` 标题在上面

`caption-side: bottom` 标题在下面

## 背景

### 背景颜色

background-color 用于设置背景颜色

`background-color: transparent` 透明背景（默认）

### 背景图片

background-image 用于设置背景图片

```css
.container{
    background-image: url(../img/flower.png);
}
```

### 背景图片重复方式

background-repeat 用于设置背景图片重复方式

`background-repeat: repeat` 不重复

`background-repeat: no-repeat` 重复铺满

`background-repeat: repeat-x` 水平方向重复铺满

`background-repeat: repeat-y` 垂直方向重复铺满

### 背景图片位置

background-position 用于设置背景图片的位置

`background-position: left` 靠左

`background-position: right` 靠右

`background-position: top` 靠顶

`background-position: bottom` 靠底

`background-position: center` 靠中间

```css
.container{
    /* 默认为左上 */
    /* 设置为右下 */
    background-position: right bottom;
    /* 只有一个维度设置，另一个默认为center*/
    background-position: right;
    /* 使用坐标来表达位置，原点为左上角，第一个数值表示横向偏移，第二个数值表示纵向偏移 */
    background-position: 20px 50px;
    /* 使用坐标来表达位置，只写一个值，表示横向偏移，纵向为center */
    background-position: 20px;
}
```

### 复合

background 用来设置背景相关属性

没有数量和顺序要求

## 鼠标

cursor 用于设置鼠标图表

`cursor: pointer` 手（可按下）

`cursor: text` 光标文本选择

`cursor: crosshair` 十字

`cursor: move` 移动

`cursor: wait` 等待

`cursor: help` 帮助

```css
.container{
    /* 使用自定义图片作为对应鼠标操作的图标 */
    cursor: url("../img/arrow.png"), pointer;
}
```

## 盒子

### 组成成分

- margin: 外边距（体积，会占据具体空间，影响其他元素的布局和自己的布局，但是不会渲染任何内容）
- border: 边框
- padding: 内边距（补白，影响内容在盒子中的位置，会渲染背景色）
- content: 内容

### 内容(content)

- `width`: 宽度
- `height`: 高度
- `min-width`: 最小宽
- `max-width`: 最大宽
- `min-height`: 最大高
- `max-height`:最大高

> 在使用范围时，具体宽度总是尽可能的大，具体高度总是尽可能的小

### 内边距(padding)

`padding-top`: 上内边距

`padding-bottom`: 下内边距

`padding-left`: 左内边距

`padding-right`: 右内边距

`padding`: 复合

```css
.container{
    /* 四个方向 */
    padding: 10px;
    /* 上下、左右 */
    padding: 10px 20px;
    /* 上、左右、下 */
    padding: 10px 20px 30px;
    /* 上、右、下、左 */
    padding: 10px 20px 30px 40px;
}
```

> padding 不能为负数
>
> 行内元素无法设置上下内边距

### 边框(border)

[详见](#边框)

### 外边距(margin)

`margin-top`: 上外边距

`margin-bottom`: 下外边距

`margin-left`: 左外边距

`margin-right`: 右外边距

```css
.container{
    /* 四个方向 */
    margin: 10px;
    /* 上下、左右 */
    margin: 10px 20px;
    /* 上、左右、下 */
    margin: 10px 20px 30px;
    /* 上、右、下、左 */
    margin: 10px 20px 30px 40px;
}
```

> margin 可以为负值

#### 技巧：居中

##### 水平居中

###### 对于块级元素

当水平方向设置auto的时候，margin会尽可能的大

当左margin和右margin都为auto的时候会水平居中

```css
.container{
    margin: 0 auto;
}
```

###### 对于行内元素/行内块元素

为父元素添加 `text-align: center`

##### 垂直居中

###### 对于块级元素

给子元素加上`margin-top`手动居中，值为：（父元素content高-子元素总高）/2

###### 对于行内元素/行内块元素

让父元素`height=line-height`，每个子元素添加上`vertical-align:middle`，如果想绝对居中，父元素设置`font-size: 0px`

#### 问题：margin塌陷

第一个子元素的上margin会作用在父元素上，最后一个子元素的下margin会作用在父元素下

解决：

- 给父元素设置不为0的padding或者不为0的border
- 给父元素设置css样式 `overflow-hidden`(BFC)

#### 问题：margin上下合并问题

兄弟元素的上下margin会合并，取最大的作为间隔

解决：

- 无需解决，一般只会设置一个兄弟的上边距或者下边距

### 处理内容溢出

overflow 用于处理溢出内容

`overflow: visible` 显示

`overflow: hidden` 隐藏

`overflow: scroll` 显示滚动条

`overflow: auto` 自动显示滚动条，不溢出不显示

### 布局模式

display 可以设置元素的布局模式

`display: block` 转化为块级元素

`display: inline-block` 转化为行内块元素

`display: inline` 转化为行内元素

`display: none` 无布局不显示，不占用空间

### 隐藏元素

visibility 可以设置是否可见

`visibility: show` 显示

`visibility: hidden` 隐藏

display 可以设置显示和布局模式

`display: none` 不显示无布局，不会占用任何空间

### 问题：元素之间存在空格

在实际代码中，不同的元素不可能总是写在一行（为了可读性），元素之间的格式化空格，缩进，回车都会被解析成空格文本

解决：

- 元素写在一行（不推荐大量使用）
- 父元素设置`font-size: 0px`

### 问题：行内块元素在盒子中下方存在空隙

行内块元素与文本的基线对齐，而文本的基线与文本的最底端存在空隙

解决：

- 给行内块设置`vertical-align`，只要不是`base-line`即可
- 给行内块设置成`display: block`
- 父元素设置`font-size: 0px`

## 浮动

浮动原本是让文字环绕图片有环绕图片的效果，但是现在更多的用于布局，现在布局上的功能已被伸缩盒模型代替

### 浮动元素的特点

- 脱离文档流
- 任何元素浮动后，宽高都由内容撑开，而且可设置宽高
- 不会独占一行
- 不会出现margin合并问题和margin塌陷问题
- 不会出现行内块元素在盒子中下方存在空隙问题

### 问题：浮动后的影响

对于兄弟元素：后面的兄弟元素，会占据浮动元素之前的位置，可能会被浮动元素覆盖

对于父元素：不能撑起父元素的高度，可能会导致父元素高度塌陷，但是依然能撑起宽度

解决：

- 给父元素指定高度
- 给父元素也设置浮动，但是父元素也会给它自己的兄弟和父元素带来影响
- 给父元素设置`overflow: hidden`(BFC)
- 在所有浮动最后面添加一个块级元素，并给该块级元素设置`clear: both`

```css
/* 对于最后一点的简便做法 */
.parent::after{
    content: "";
    display: block;
    clear: both;
}
```

> 布局原则：设置浮动时候，兄弟元素要么全部浮动，要么全部不浮动

## 定位

### 相对定位

参考点：自己原来的位置

给元素设置`position: relative` 可将元素作为相对定位元素显示

相对定位显示会覆盖别的元素，后写的相对定位元素会覆盖先写的相对定位元素

只是视觉上的变化，实际位置不变，不会影响布局

```css
.container{
    position: relative;
    top: 50px;
    /* 可为负数 */
    left: -50px;
    /* bottom: 50px */
    /* right: -50px */
}
```

### 绝对定位

参考点：包含块的位置

> 包含块：向上搜索，第一个具有定位属性的祖先元素

给元素设置`position: absolute` 可将元素作为绝对定位元素显示

不再在文档流之中

```css
.container{
    position: absolute;
    top: 50px;
    /* 可为负数 */
    left: -50px;
    /* bottom: 50px */
    /* right: -50px */
}
```

### 固定定位

参考点：浏览器页面视口

一般用于广告，导航栏

给元素设置`position: fixed` 可将元素作为固定定位元素显示

不再在文档流之中

```css
.container{
    position: fixed;
    top: 50px;
    /* 可为负数 */
    left: -50px;
    /* bottom: 50px */
    /* right: -50px */
}
```

### 粘性定位

参考点：向上搜索，最近一个具有滚动条的父元素

一般用于广告，导航栏，侧边栏

可以完整的显示该元素的时候，不会发生任何事情

父元素滚动之后，粘性元素显示不全或者无法显示的时候，会按照设置的值进行定位

多个粘性定位元素，下一个粘性定位元素会挤掉上一个粘性定位元素

```css
.container{
    position: sticky;
    /* 一般只设置top值 */
    top: 50px;
    /* 可为负数 */
    /* left: -50px; */
    /* bottom: 50px */
    /* right: -50px */
}
```

### 定位层级

`z-index` 设置显示层级，默认为0

定位层级比较优先级如下

1. 包含块层级高的子元素 > 包含块显示层级低的子元素
2. 显示层级高的元素 > 显示层级低的元素
3. 后写的定位元素 > 先写的定位元素
4. 定位元素 > 无定位元素

### 技巧：充满包含块

当不设置定位元素宽高，但是同时设置了left, right属性为0或top, bottom属性为0，那么盒子会自动拉伸到整个包含块

### 技巧：居中

同时设置top, bottom或者left, right然后再设置`margin: auto`，那么margin会自动拉伸，使得content, padding, border组成的盒子居中
