---
title: SCSS 学习笔记
published: 2026-10-19
description: SCSS 语法和样式组织方式整理。
tags: [SCSS, CSS, 前端]
category: 前端
draft: false
---

# SCSS

# SASS/SCSS 作用

> Vite 项目安装 `sass`（注意：vite 里包名就叫 `sass`，不是 `node‑sass`）
> `.scss` 就是 sass 的语法。 普通 css 是静态语言，SCSS 在 CSS 基础上增加编程能力。

## 核心能力

### 变量 `$`

```scss
// scss
$primary-color: #409eff;
$font-size-base: 14px;

.box {
  color: $primary-color;
  font-size: $font-size-base;
}
```

css 原生变量是 `var()`，scss 变量是编译阶段就直接替换成真实值。

### 嵌套写法（写 vue scoped 样式超级常用）

```scss
// scss
.card {
  width: 200px;
  .title {
    font-size: 16px;
  }
  &:hover {
    background: #eee;
  }
}
```

编译输出普通 css：

```
.card { width:200px; }
.card .title { font-size:16px; }
.card:hover { background:#eee; }
```

`&` 代表父选择器，写组件样式少写大量重复类名。

### mixin 混入（可带参数，复用样式片段）

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.box {
  @include flex-center;
}
```

### @import 分模块管理样式

可以把变量、mixin 抽成单独文件，全局导入，不用每个组件重复写。 `src/styles/variables.scss` 存放主题色、间距、尺寸。

### 运算

```scss
$base:10px;
.item {
  width: $base * 2;
}
```

---

## 和普通 CSS 对比

- 普通 CSS：没有变量、没有嵌套、不能写函数，代码重复多。
- SCSS：**编译期预处理器**，vite 内部自动编译 scss 输出原生 css，浏览器不认识 scss，最终打包产物还是 css。

## 在 Vue3+Element‑Plus 后台项目里的实际用处

1. 组件 `<style lang="scss" scoped>` 开启 scss 语法，支持嵌套，写组件样式更舒服。
2. 统一管理全局主题变量：主色、间距、圆角、阴影。
3. 封装 mixin，比如居中、文本省略、清除浮动，各个组件直接复用。
4. 配合 Element‑Plus 可以**覆盖修改 element plus 默认主题颜色**。

```
<style lang="scss" scoped>
.home-page {
  padding: 20px;
  .wrapper {
    background: #fff;
  }
}
</style>
```

> `lang="scss"` 就依赖 sass 包，不装会直接报错。
