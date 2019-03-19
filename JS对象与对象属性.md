# JS对象与对象属性

---

**JavaScript 对象**
1. 对象是一种复合值：将很多值复合在一起（包括原始类型值、对象、函数）
2. 对象是若干无序属性的集合，可以直接通过属性名来访问对象的属性（键值对）
3. 函数作为某一个对象的属性时，称其为该对象的方法

**对象的重要性**
 1. 一切数据都是通过变量（标识符）保存
 2. 对象将相应的数据封装在一起统一管理
 
**属性的重要性**
操作数据就是操作对象的属性

**对象分类**
1. 内置对象（native object）
由 ECMAScript 规范定义的对象或构造器对象（数组、函数等）
2. 宿主对象（host object）
由 JavaScript 解析器所嵌入的宿主环境定义的（如：window、document）
3. 自定义对象（user-defined object）
运行中的用户自定义JS代码创建的对象
[图片](https://github.com/asx112/Blog/blob/master/%E5%AF%B9%E8%B1%A1%E5%88%86%E7%B1%BB.png)

**属性的种类**
1. 数据属性（Property）
 对象中的普通属性，从字符串的键到值的映射，是最常见的属性类型。
2. 访问器属性（Accessor）
类似于读、写属性的特殊方法，访问器可以计算属性的值。
3. 内置属性（Internal  property）
只存在于ECMAScript语言规范中，不能直接访问，有可能存在间接访问方式。规范将内置属性的键置于方括号中。比如[[Scope]]、[[Prototype]]
____proto____可以访问[[Prototype]]

**对象和属性操作**
1. 定义对象
2. 定义属性
3. 访问属性
属性访问方式: 对象名.属性名; 对象名["属性名"]
（.）点操作符: 属性的键必须是标识符
（[]）中括号操作符: 通过表达式计算并强制转换为字符串类型的键访问属性
4. 添加属性
5. 修改属性
6. 删除属性
7. 遍历属性

**属性特性**
[图片](https://github.com/asx112/Blog/blob/master/%E5%B1%9E%E6%80%A7%E7%89%B9%E6%80%A7.png)

**数据属性的特性**
1. value（属性的值）：对应属性的值
2. writable（可写特性）	：确定属性是否可改写性
3. configurable（可配置特性）：确定属性是否能删除和其他特性是否可配置
4. enumerable（可枚举特性）：属性是否可枚举

**属性描述符（property descriptor）**
1. 属性特性描述符是一个用来查看对象属性的特性的对象，该对象包含4个属性，对应4个特性
2. 封装了属性特性的对象，方便实现数据属性特性的设置和查询
[图片](https://github.com/asx112/Blog/blob/master/%E5%B1%9E%E6%80%A7%E6%8F%8F%E8%BF%B0.png)

**设置属性描述符**
1. Object.defineProperty(obj, prop, descriptor)
obj —— 要在其上定义属性的对象。
prop —— 要定义或修改的属性的名称。
descriptor —— 将被定义或修改的属性描述符
value 默认为 undefined
enumerable、writable、configurable 默认为 false
2.  Object.defineProperties(obj, props)
obj —— 要在其上定义属性的对象。
props —— 要定义属性及属性描述符的对象。
3. 字面量定义默认属性特性为 true

**查询属性描述符**
1. Object.getOwnPropertyDescriptor(obj,prop) 方法
返回指定对象上一个自有属性对应的属性描述符。
obj —— 需要查找的目标对象
prop —— 目标对象内属性名称
2. Object.getOwnPropertyDescriptors(obj) 
获取一个对象的所有自身属性的描述符

**enumerable：枚举性**
1. 一般来说，系统创建的属性不可枚举，而用户创建的属性可枚举。
2. 通常不应该给内置原型和对象添加属性和方法。如果需要添加，应该设置属性不可枚举，避免破坏现有代码
3. 枚举的主要目的是判断 for-in 循环中的那些属性应该被忽略。
4. 枚举性影响的操作： for-in 循环；  Object.keys()； JSON.stringify()
5. obj.propertyIsEnumerable(prop) 
返回一个布尔值，表示指定的属性是否可枚举。

**configurable：可配置特性**
 确定属性是否能删除和其他特性是否可配置

**定义属性**
1. 如果属性不存在，会创建一个新的属性，它的特性由描述符指定，若果未指定，则使用默认值。
2. 如果属性已经存在，会更新描述符指定的属性特性。但是描述符中的特性没有对应的特性，则特性不变。

**访问器属性的特性**
1. get：读取属性时调用的函数，该函数计算读取的结果，默认是 undefined
2. set: 设置属性值时调用的函数，该函数接受设置的值作为参数，默认是undefined
3. configurable（可配置特性）：确定属性是否能删除和其他特性是否可配置
4. enumerable（可枚举特性）：属性是否可枚举
5. 访问器属性（存取器属性）定义一个或两个和属性同名的函数，这个函数定义没有使用 function 关键字，而是使用 get 和 set。
6. 属性名和函数体没有冒号分隔。
7. 函数体结束和下一个属性有逗号分隔。
8. JavaScript 把这些函数当做对象的方法调用，函数中的 this 指向这个对象。

**设置属性特性**
Object.defineProperty()
Object.defineProperties()

**获取属性特性**
Object.getOwnPropertyDescriptor() Object.getOwnPropertyDescriptors(）

**属性特性默认值**
属性值|默认值
--|--
Value|undefined
Get|undefined
Set|undefined
Writable|false
Enumerable|false
Configurable|false






