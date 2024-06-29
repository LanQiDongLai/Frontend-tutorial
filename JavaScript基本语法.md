## 基本语法风格

风格总体为C类语言风格

### 分号

分号可以加可以不加，但是在某些情况下不加分号可能会造成歧义，建议加上

### 注释

与C类语言一致

```javascript
// 单行注释
/*
	多行注释
*/
```

### 声明式

```javascript
// 可变变量
let message = "Hello";
// 可变变量
var config = "DEBUG";
// 常量
const PI = 3.1415926;
```

> `let`和`var`的区别
>
> `let`声明的变量
>
> - 具有块作用域
> - 具有先后顺序
> - 与常见的其他的语言中的变量类似
>
> `var`声明的变量
>
> - 没有块作用域，只有函数作用域和全局作用域，在块中声明，块外部仍然可见
> - 在后面声明，前面依然可用，但是值为`undefined`
> - 可以在同作用域中重新声明同名变量（变量遮蔽）

### 动态类型

动态类型允许变量在运行期变换自己的类型

```javascript
let variable = "String";
variable = 1; // 不会报错
```

### 引号

在JavaScript中单引号和双引号没有区别，交替使用可以防止字符串中引号歧义

反引号允许使用`${str}`在字符串中嵌入变量和表达式

```javascript
// 防止歧义
let message = 'You know, his name is "John"';
// 内嵌表达式
let num1 = 6, num2 = 10;
let result = `the result is ${num1 + num2}`;
```

## 数据类型

### 原始数据类型

#### 数字类型（number）

与常规语言类似，该类型可以表示整数，也可以表示浮点数，存储结构为64位双精度浮点数（IEEE 754）

```javascript
let num = 1.2;
```

在进行数字运算的时候，JavaScript永远不会因为错误而崩溃，因为内置的`Infinity`、`-Infinity`和`NaN`的特殊数字类型

- `Infinity` 正无穷大
  - 当正数除以0的时候，返回该结果
  - 当对`Infinity`进行加减乘除运算的时候，返回此结果
  - 当对`-Infinity`取相对数的时候，返回此结果
  - 算术运算的结果太大溢出时，返回此结果
- `-Infinity` 负无穷大
  - 参考正无穷大
- `NaN` 非数
  - 当对一个无法转化为数字类型的类型进行强制转换，返回此结果
  - 当对一个无法转化为数字类型的类型进行数字运算，返回此结果
  - `0 / 0`，返回此结果
  - 库自定义的非法数字运算，返回此结果

#### 大整数类型（bigint ）

无大小限制，只能存储整数

```javascript
// 结尾n后缀表示此类型为大数类型
let big_num = 1231211327856425873456348573546394856n;
```

#### 字符串类型（string）

#### 布尔类型（boolean）

#### 空值（null）

#### 未定义（undefined）

#### 符号类型（symbol）

### 复杂数据类型（对象类型）

#### 类类型（object）

#### 数组（array）

#### 函数类型（function）

### 查看类型

使用`typeof`来查看数据类型，返回的字符串和上述的变量一致，有两个除外（null，array）

```javascript
let num = 1;
// 下面两种方法都行
console.log(typeof num);
console.log(typeof(num));

// 输出object，这里其实是历史遗留问题
console.log(typeof(null));
// 输出object，因为数组继承于Object
console.log(typeof([1, 2, 3]))
```

## 类型转换