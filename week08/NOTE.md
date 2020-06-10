# Week08 重学 CSS

## 一、选择器

### 1. 选择器语法

#### 简单选择器

- \*
- div svg|a
  c
- .cls
- #id
- [attr=value]
- :hover
- ::before

#### 复合选择器

- <简单选择器><简单选择器><简单选择器>
- \*或者 div 必须写在最前面

#### 复杂选择器

- <复合选择器>\<sp\><复合选择器>
- <复合选择器>">"<复合选择器>
- <复合选择器>"~"<复合选择器>
- <复合选择器>"+"<复合选择器>
- <复合选择器>"||"<复合选择器> (level 4)

### 2. 选择器优先级

[inline, id, class, tag]

### 3.伪类

- 链接/行为

  - :any-link
  - :link:visited
  - :hover
  - :active
  - :focus
  - :target

- 树结构

  - :empty
  - :nth-child()
  - :nth-last-child()
  - :first-child :last-child :only-child

- 逻辑型
  - :not 伪类
  - :where :has

### 4.伪元素

- before
- after
- first-letter
- first-line

### 5.排版

#### 盒 (box)

- 盒模型
- 正常流 (Normal Flow)
