# Week09 总结——重学 CSS

## 动画与绘制

### Animation

- @keyframes 定义
- animation: 使用

属性

- animation-name
- animation-duration
- animation-timing-function
- animation-delay
- animation-iteration-count
- animation-direction

### Transition

- transition-property
- transition-duration
- transition-timing-function
- transition-delay

#### Timing Function —— cubic-bezier

预设

- ease: 平滑，适合移动，最常用
- linear: 匀速，不常用
- ease-in：适合退出

知识点：

- 动画性能：Use `transform` instead of `left` / `top`
- GPU 计算：`transform 3d` / `transform 2d`

### 颜色

- RGB
- CMYK
- HSL
- HSV

### 形状

- border
- box-shadow
- border-radius
- data uri + svg 矢量图

---

## css 总结

### css property

- layout
- interactive
- render/draw
- svg
- other

获取全部 css 属性
getComputedStyle(document.body)
(去除 -webkit- 前缀)
