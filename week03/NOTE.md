# Week3 总结：JavaScript 表达式/类型转换、语句/对象

## Expression (表达式)

> ECMA-262: P201 12.3

### Member Expression (访问属性/成员)

- a.b
- a[b]
- foo\`string\`
- subper.b
- super['b']
- new.target
- new Foo()

> Member Expression 返回的是一个 Reference 对象

- Reference

  - Object
  - Key
  - 写权限只有 delete, assign

  ```javascript
  // Reference的类似实现
  class Reference {
    constructor(object, property) {
      this.object = object;
      this.property = property;
    }
  }
  ```

- New
- Call
  - foo()
  - super()
  - foo()['b']
  - foo().b
  - foo()`abc`

> 有函数调用参与的 member expression 中，函数调用的优先级比 New 更低 Example:
> `new a()['b']` 这里会先 new 再取值

### 其他

1. 用 void 0 表示 undefined, 防止局部变量的覆盖
2. 判断正负 0，代码如下：

```javascript
function check(zero) {
  if (1 / zero === Infinity) {
    return 1;
  }
  if (1 / zero === -Infinity) {
    return -1;
  }
}
```

#### Tree vs Priority

从使用语言的角度来看是表达式的优先级
从语言实现的角度来看是树结构

### 语句

语句分为简单语句和复合语句

#### 简单语句

- ExpressionStatement ( a = 1 + 2 )
- EmptyStatement ( ; )
- DebuggerStatement ( debugger )
- ThrowStatement ( throw )
- ContinueStatement ( continue )
- BreakStatement ( break )
- ReturnStatement ( return )

#### 复合语句(由简单语句复合而来)

- BlockStatement ( {...somecode} )
- IfStatement ( if(){...somecode} )
- IterationStatement
- VariableStatement

#### 对象

- Object 属性值有 Data 和 Accessor，其中数据属性值用于描述状态，访问器属性用于描述行为。数据属性值中如果存储函数，也可以用于描述行为。
- 除了常见的 Object 是对象之外，Array、Function 都是特殊的对象。其中 Array 就是带有`[[length]]`属性的对象；Function 就是带有`[[Call]]`内置属性的对象

### JS 标准里面有哪些对象是我们无法实现的，都有哪些特性

- Bound Function Exotic Objects
  - `[[Call]]`
  - `[[Construct]]`
- Array Exotic Objects
  - `[[DefineOwnProperty]]`
  - `ArrayCreate(length[,proto])`
  - `ArraySpeciesCreate(originalArray,length)`
  - `ArraySetLength(A,Desc)`
- String Exotic Objects
  - `[[GetOwnProperty]]`
  - `[[DefineOwnProperty]]`
  - `[[OwnPropertyKeys]]`
  - `StringCreate(value,prototype)`
  - `StringGetOwnProperty(S,P)`
- Arguments Exotic Objects
  - `[[GetOwnProperty]]`
  - `[[DefineOwnProperty]]`
  - `[[Get]]`
  - `[[Set]]`
  - `[[Delete]]`
  - `CreateUnmappedArgumentsObject(argumentsList)`
  - `CreateMappedArgumentsObject(func,formals,argumentsList,env)`
- Integer-Indexed Exotic Objects
  - `[[GetOwnProperty]]`
  - `[[HasProperty]]`
  - `[[DefineOwnProperty]]`
  - `[[Get]]`
  - `[[Set]]`
  - `[[OwnPropertyKeys]]`
  - `IntegerIndexedObjectCreate(prototype,internalSlotsList)`
  - `IntegerIndexedElementGet(O,index)`
  - `IntegerIndexedElementSet(O,index,value)`
- Module Namespace Exotic Objects
  - `[[SetPrototypeOf]]`
  - `[[IsExtensible]]`
  - `[[PreventExtensions]]`
  - `[[GetOwnProperty]]`
  - `[[DefineOwnProperty]]`
  - `[[HasProperty]]`
  - `[[Get]]`
  - `[[Set]]`
  - `[[Delete]]`
  - `[[OwnPropertyKeys]]`
  - `ModuleNamespaceCreate(module,exports)`
- Immutable Prototype Exotic Objects
  - `[[SetPrototypeOf]]`
  - `SetImmutablePrototype`
