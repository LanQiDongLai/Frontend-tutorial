#### 对象声明

对象本质上可以看做是一组键值对，键称为属性名，值称为属性值

```javascript
let user = {
    name: "John",
    age: 18,
    // 属性名存在特殊符号必须写双引号
    "email address": "xxx@163.com",
}
// 也可以这么声明一个对象
let user = new Object();
```

当然也可以这样声明

```javascript
let fruit = "apple";
let bag = {
    // 动态属性名
    [fruit]: 3,
}

// 属性名与属性值变量相同的简写
function makeUser(name, age){
    return {
        name, // 自动扩展为name:name
        age,  // 自动扩展为age:age
    };
}
```

#### 对象属性的增删改查、存在性测试与遍历

- 查

```javascript
// 通过点进行访问属性名对应的值
console.log(user.name);
// 通过中括号进行访问属性名对应的值，如果属性名存在特殊符号，那么该属性值必须通过该方式进行访问
console.log(user["email address"]);
// 如果对象不包含该属性，那么将返回undefined
console.log(user["isAdmin"]); // undefined
```

- 改

```javascript
// 当该属性名存在于对象中，通过直接赋值的方式可以更改属性值
user.age = 19;
```

- 增

```javascript
// 当该属性名不存在于对象中，通过直接赋值的方式可以插入新的属性
user.score = 100;
```

- 删

```javascript
// 通过delete删除该对象的某个属性
delete user.score;
```

- 存在性测试

```javascript
// 测试是否存在该属性
let res = ("name" in user); // true
```

- 遍历

```javascript
// for in 循环进行遍历对象所有的属性名
for(let key in user){
    console.log(key); // name age
}
```

#### 对象属性访问可选链

在访问对象的属性时，如果不存在该属性会返回`undefined`，当尝试访问undefined的属性那么会报错

```javascript
let user = {};
console.log(user.address.street); // ERROR：尝试访问原始类型undefined的street属性
```

使用可选链可以提前把undefined返回，避免报错

```javascript
let user = {};
console.log(user?.address?.street); // undefined
```

如果属性值为null也会提前返回undefined

```javascript
let user = {address: null};
console.log(user?.address?.street); // undefined
```

变体

```javascript
user?.[adress] // 可选属性，与上文相同，不过是以方括号方式访问属性
user.say?.(); // 可选方法，存在及调用，不存在则返回undefined
```

#### 对象属性顺序

当属性名可以转化为**整数**的时候，该属性提前，并按照从小到大的形式进行排序

```javascript
let arr = {
    0: 1,
    length: "3",
    name: "array",
    1: 2,
    2: 3,
}
// 存储形式
let arr = {
    0: 1,
	1: 2,
    2: 3,
    length: "3",
    name: "array",
}
```

#### 对象的复制

##### 引用复制

注意对象名只存储了指向对象实际地址的引用，当复制时，对象并不会拷贝一份

```javascript
let user1 = {
    name: "John",
    age: 18,
};
let user2 = user1;
// 修改user2的内容，user1却也发生变化，说明他们所代表的是同一个对象
user2.name = "Lan";
console.log(user1.name); // Lan
```

对象之间可以通过`===`来判断引用是否为同一对象

##### 浅复制

通过`Object.assign(dst, [src1, src2, ...])`方法来赋值

该方法会将`src`列表中所有属性添加到`dst`中，并返回`dst`

```javascript
let user2 = Object.assign({}, user1);
// 或者这么写
Object.assign(user2, user1);
```

##### 深复制

浅复制对对象中的对象仍然是引用复制，所以需要递归实现对子对象的复制

自己通过递归实现深复制功能，或者通过第三方库来调用，例如 [lodash](https://lodash.com/)库的[.cloneDeep(obj)](https://lodash.com/docs#cloneDeep)

#### 对象方法

对象方法在对象中为一个属性，由函数名（属性名）和函数表达式（属性值）组成

对象方法声明可以采取函数表达式或者函数声明式

```javascript
// 方法声明
let user = {
    say: function(){
        console.log("Hello");
    }
};
// 简写
let user = {
    say(){
        console.log("Hello");
    }
};
```

`this`指针，与绝大多数编程语言不同，`this`指针的值只有在所在被调用的时候才会指向对象

```javascript
let user = { name: "John" };
let admin = { name: "Admin" };

function getName() {
  console.log(this.name);
}
// 在两个对象中使用相同的函数
user.getName = getName;
admin.getName = getName;
// 函数是一致的，但是当函数调用时，会自动检索函数所属的对象，并为其中的this赋值
getName(); // undefined(this == undefined)
user.getName(); // John(this == user)
admin.getName(); // Admin(this == admin)
```

#### 构造方法

构造方法与对象方法类似，但区别是构造方法不存在于对象之中，并且调用时采用`new`来调用

```javascript
function User(){
    this.name = "John";
    this.age = 18;
}
let user = new User();
```

当对一个函数进行`new`操作调用的时候，会隐式扩展如下内容

```javascript
function User{
    // this = {}
    this.name = "John";
    this.age = 18;
    // return this;
}
```

如果函数体中存在自带的`return`语句那么会出现以下情况

- 如果返回为原始类型则忽略
- 如果返回为对象则忽略`return this;`，直接返回

#### 符号（Symbol）

##### 符号意义

我们可以使用字符串作为属性名，也可以用符号`Symbol`作为属性名

相同描述的符号是不同的，每个符号创建后都是唯一的

```javascript
let nameSymbol = Symbol("name");
// 使用Symbol作为属性名
let user = {
    [nameSymbol]: "John",
};
// 通过相同的Symbol访问
console.log(user[nameSymbol]); // John
// 符号是唯一的，即使描述相同
let nameSymbol2 = Symbol("name");
console.log(user[nameSymbol2]); // undefined
```

这样做的好处是可以防止使用字符串添加属性会修改对象本身固有的属性

```javascript
let nameSymbol = Symbol("name");
let user = {
    [nameSymbol]: "John",
};
user["name"] = "Mike";
// 原属性没有受到影响
console.log(user[nameSymbol]); // John
```

##### 特征

符号类型无法自动转化为字符串，但是可以用如下方法进行转换

```javascript
let nameSymbol = Symbol("name");
console.log(nameSybol.toString()); // Symbol(name)
console.log(nameSybol.description; // name
```

符号会隐藏在一般的遍历方法中，如`for in` `Object.keys(obj)`，但是可以使用`Object.getOwnPropertySymbols(obj)`来获取

```javascript
// 无法找到隐藏着的符号，直接跳出
for (let key in user){
    console.log(key.toString());
}
// 使用getOwnPropertySymbols来获取所有Symbol
let symbols = Obeject.getOwnPropertySymbols(user);
for(let symbol of symbols){
    console.log(symbol.toString());
}
```

##### 全局符号

使用`Symbol.for`来注册或获取一个全局符号

```javascript
 // 如果该 symbol 不存在，则创建它
let id = Symbol.for("id");
// 再次读取（可能是在代码中的另一个位置）
let idAgain = Symbol.for("id");
// 相同的 symbol
alert( id === idAgain ); // true
```

使用`Symbol.keyFor`来获取一个全局符号所持有的名称

```javascript
// 等效于 id.description
console.log(Symbol.keyFor(id));
```

##### 系统符号

用于实现对象中通用的特性，例如

- `Symbol.hasInstance`
- `Symbol.isConcatSpreadable`
- `Symbol.iterator`
- `Symbol.toPrimitive`
- ...

详见[系统Symbol符号表](https://tc39.es/ecma262/#sec-well-known-symbols)

系统符号中的一种用途详见下一段

#### 原始类型转换方法

当对象包含了`Symbol.toPrimitive`属性，那么会在自动类型转换的时候调用该属性的方法

```javascript
// 定义对象自动转换为原始类型的方式
let obj = {
  [Symbol.toPrimitive](hint) {
    if (hint === 'number') {
      return 10;
    }
    return 'default';
  }
};
// 等效于console.log(obj[Symbol.toPrimitive("number")]);
console.log(+obj);  // 10
// 等效于console.log(obj[Symbol.toPrimitive("string")]);
console.log(`${obj}`);  // 'default'
```

如果不存在`Symbol.toPrimitive`，那么会自动检索`valueOf`和`toString`属性

如果要转换的类型是`number`那么先调用`valueOf`，其次是`toString`后再转换成`number`

如果要转换的类型是`string`那么先调用`toString`，其次是`valueOf`后再转换成`string`
