# 第 2 周总结 —— JavaScript 语言设计、词法、类型

## 编程语言通识

### 语言按语法分类

- 非形式语言
  - 中文，英文
- 形式语言（乔姆斯基谱系）
  - 0 型 无限制文法
  - 1 型 上下文相关文法
  - 2 型 上下文无关文法
  - 3 型 正则文法

### 产生式(BNF)

> BNF: 巴科斯范式

- 用尖括号扩起来的名称来表示语法结构名
- 语法结构分成基础结构和需要用
  - 基础结构称终结符
  - 复合结构称非终结符
- 引号和中间的字符表示终结符
- 可以有括号
- \* 表示重复多次
- \| 表示或
- \+ 表示至少一次

#### 其他产生式

EBNF ABNF Customized

> JS ECMA262 重点 Grammar Summary

### 图灵完备性

- 命令式——图灵机
  - goto
  - if 和 while
- 声明式——lambda
  - 递归

### 动态与静态

- 动态：
  - 在用户的设备 / 在线服务器上
  - 产品实际运行时
  - Runtime
- 静态：
  - 在程序员的设备上
  - 产品开发时
  - Compiletime

### 类型系统

- 动态类型系统与静态类型系统
- 强类型与弱类型（有隐式类型转换的是弱类型）
  - String + Number
  - String == Boolean
- 复合类型
  - 结构体：{ a: T1, b: T2 }
  - 函数签名: (T1, T2) => T3
- 子类型
  - 逆变 / 协变

### 一般命令式编程语言

## unicode

- Blocks: 按字符块划分，例如 ASCII，CJK
- Category: 按种类划分，例如 space, letter

## Lexical Grammar（词法）

InputElement

- WhiteSpace (空白)

  - TAB
  - VT (纵向 Tab)
  - FF （Form Feed）
  - SP （普通空格）
  - NBSP (no-break space)
  - ZWNBSP(Zero width no-break space)

- LineTerminator（换行符）
  - LF (line feed -> \n)
  - CR (carriage return -> \l)
  - ...
- Comment（注释）
- Token
  - Punctuator 符号，例如 > , < ;
  - IdentiFierName
    - keywords 关键字，例如 let for
    - Identifier 标识符：例如：变量名、属性
    - Future reserved Keywords 保留字 enum
  - Literal 直接量（字面量）例如：100 true
    - Number
    - String
    - ...

> 1. Token 可以理解为 JavaScript 中有效的词
> 2. 变量名不能和关键字重名，属性名可以
> 3. 自己写代码时将字符控制在 ASCII 是最佳实践

### Number Grammar

支持的语法：

- Decimal Literal (十进制)
  - 0
  - 0\.
  - \.2
  - 1e3
- Binary Integer Literal (二进制整数)
  - 0b111
- Octal Integer Literal (八进制整数)
  - 0o10
- Hex Integer Literal (十六进制整数)
  - 0xFF

### Number Practice

- Safe Integer
  - Number.Max_SAFE_INTEGER.toString(16)
  - "1fffffffffffff"
- Float Compare
  - Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON

### String

- Charactor
- Code Point
- Encoding
  - UTF8
  - UTF16

字符集：

- ASCII
- Unicode
- UCS U+0000 - U+FFFF
- GB (国标 - 中文)
  - GB2312
  - GBK(GB13000)
  - GB18030
- ISO-8859 (欧洲字符)
- BIG5 (繁体中文)

### String Grammar

- ''
- ""
- `` (Template)

EscapeCharacter : \t \n ...

### Boolean

- true
- false

### RegExp Literal

- 可用除法时解析为除法，其他情况为正则直接量
