### 新增布局标签

| 标签    | 语义                     | 说明     |
| ------- | ------------------------ | -------- |
| header  | 整个页面，或部分区域头部 | 块级元素 |
| footer  | 整个页面，或部分区域底部 | 块级元素 |
| nav     | 导航                     | 块级元素 |
| article | 文章                     | 块级元素 |
| section | 文章段                   | 块级元素 |
| aside   | 侧边栏                   | 块级元素 |

### 新增状态标签

- `meter` 用于表示数值范围，尺度，一般用于水位线，电池电量等显示
  - 属性: high 规定高值
  - 属性: low 规定低值
  - 属性: max 规定最大值
  - 属性: min 规定最小值
  - 属性: optimum 规定最优值
  - 属性: value 规定当前值
- `progress` 用于表示进度指示，一般用于进度条，工作进度等
  - 属性: max 表示目标值
  - 属性: value 表示当前值

### 新增列表标签

#### 搜索提示

| 标签     | 语义                                       | 说明     |
| -------- | ------------------------------------------ | -------- |
| datalist | 用于搜索框关键词提示，内部元素为option选项 | none元素 |

```html
<input type="search" name="wd" list="recommand">
<datalist id="recommand">
    <option>How to screenshot on windows</option>
    <option>How to recall email in outlook</option>
    <option>How many countries in the world</option>
</datalist>
```

#### 拉伸列表

| 标签    | 语义                                        | 说明          |
| ------- | ------------------------------------------- | ------------- |
| details | 用于显示问题与答案，或者对专有名词的解释    | 块级元素      |
| summary | 存在于`<details>`中用于表示专有名词或者问题 | list-item元素 |

```html
<details>
    <summary>How to solve this question?</summary>
    <p>Just solve it</p>
</details>
```

### 新增文本标签

#### 文本注音

| 标签 | 含义                 | 说明          |
| ---- | -------------------- | ------------- |
| ruby | 包裹需要注音的文字   | ruby元素      |
| rt   | 注音，存在于`ruby`中 | ruby-text元素 |

```html
<ruby>
    <span>汉字</span>
    <rt>han zi</rt>
</ruby>
```

#### 文本标记

| 标签 | 含义                         | 说明     |
| ---- | ---------------------------- | -------- |
| mark | 一般用于搜索结果中的文本标记 | 行内元素 |

### 新增表单控件属性

| 属性         | 含义                       | 说明                                                   |
| ------------ | -------------------------- | ------------------------------------------------------ |
| placeholder  | 提示文字                   | 文字输入类控件可用                                     |
| require      | 输入项必填                 | 用于除了按钮之外的控件                                 |
| autofocus    | 自动获取焦点               | 可用于所有表单控件                                     |
| autocomplete | 浏览器可记忆，下次自动完成 | 文字输入类控件可用，除了密码和多行文本                 |
| pattern      | 正则验证                   | 文字输入类控件可用，除了多行文本，当输入框为空时不验证 |

### 新增input的type属性

| type           | 含义                 | 说明                                                         |
| -------------- | -------------------- | ------------------------------------------------------------ |
| email          | 邮件地址输入栏       | 会验证格式，但是为空则不会验证                               |
| url            | 地址输入栏           | 会验证格式，但是为空则不会验证                               |
| number         | 数值调整栏           | 附加属性step（每次调整步长），max（最大值），min（最小值），value（当前值） |
| search         | 搜索栏               |                                                              |
| tel            | 电话                 | 会验证格式，但是为空则不会验证                               |
| range          | 范围滑动栏           | 附加属性min（最小值），max（最大值），value（当前值）        |
| color          | 颜色拾色器           |                                                              |
| date           | 日期选择器（日历栏） |                                                              |
| month          | 月份选择器           |                                                              |
| week           | 周选择器             |                                                              |
| time           | 时间（分秒）选择器   |                                                              |
| datetime-local | 日期时间选择器       |                                                              |

### 视频标签

video 用于定义视频

| 属性     | 含义            | 说明                                                         |
| -------- | --------------- | ------------------------------------------------------------ |
| src      | url地址         |                                                              |
| width    | 视频播放器宽度  |                                                              |
| height   | 视频播放器高度  |                                                              |
| controls | 显示视频控件    |                                                              |
| muted    | 视频静音        |                                                              |
| autoplay | 自动播放        |                                                              |
| loop     | 循环播放        |                                                              |
| poster   | 视频封面url地址 |                                                              |
| preload  | 是否预加载      | 可包含值auto（预加载视频）, none（不做预加载）, metadata（仅预加载元信息） |

> 当视频没有设置静音时，且设置了自动播放，那么浏览器会自动静音

### 音频标签

audio 用于定义音频

| 属性     | 含义         | 说明                                                         |
| -------- | ------------ | ------------------------------------------------------------ |
| src      | url地址      |                                                              |
| controls | 显示音频控件 |                                                              |
| muted    | 音频静音     |                                                              |
| autoplay | 自动播放     |                                                              |
| loop     | 循环播放     |                                                              |
| preload  | 是否预加载   | 可包含值auto（预加载视频）, none（不做预加载）, metadata（仅预加载元信息） |

### 新增全局属性

| 属性            | 含义                       | 说明           |
| --------------- | -------------------------- | -------------- |
| contenteditable | 内容是否可以被编辑         | 值：true false |
| draggable       | 元素是否可以被拖动         | 值：true false |
| hidden          | 隐藏元素                   |                |
| spellcheck      | 是否检查拼写               | 值：true false |
| contextmenu     | 设置右键菜单               |                |
| data-*          | 用于存储页面的私有定制数据 |                |

### 兼容性处理

添加如下代码，让浏览器处于最优渲染模式

```html
<!-- 设置IE总是使用最新的文档模式进行渲染 -->
<meta http-equiv="X-UA-Comatible" content="IE=Edge">
<!-- 优先使用webkit(Chromium)内核进行渲染 -->
<meta name="render" content="webkit">
```

使用html5shiv让低版本的浏览器也能认识部分H5语义化标签

```html
<!-- [if lt ie 9]>
    <script src="../source/js/html5shiv.js"></script>
<![endif]-->
```

