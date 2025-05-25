# 北京大学 Typst 幻灯片模板 (PKU Typst Slides)

一个简洁、专业的北京大学 Typst 演示文稿模板，适用于学术报告、课程演示等场景。本项目参考LaTeX类似模板，使用Typst重新制作，更简洁高效。

![北京大学校徽](assets/images/pku-logo.png)

## 📚 目录

- [简介](#简介)
- [特性](#特性)
- [快速开始](#快速开始)
- [基本用法](#基本用法)
- [高级功能](#高级功能)
- [自定义修改](#自定义修改)
- [常见问题](#常见问题)

## 📖 简介

这是一个基于 [Typst](https://typst.app/) 排版系统开发的北京大学演示文稿模板，提供了简洁美观的幻灯片设计，内置北大标准配色和校徽，支持中文字体显示，适合各类学术汇报和教学演示场景。

Typst 是一种现代排版系统，相比 LaTeX 更加简洁易用，同时保持了高质量的排版效果。该模板利用 Typst 的特性，为北大师生提供了一个易于使用的演示文稿解决方案。

## ✨ 特性

- 🎨 内置北大标准红蓝配色方案
- 🏫 集成北大校徽图标
- 🇨🇳 完善的中文字体支持
- 📊 多种排版元素（表格、代码块、公式等）
- 📑 自动生成目录页
- 📐 专业的学术演示布局
- 🛠️ 丰富的自定义选项
- 📱 4:3 标准演示文稿比例

## 🚀 快速开始

### 环境要求

- 安装 [Typst](https://typst.app/) 排版系统
- 确保系统中安装了适当的中文字体（模板默认使用 "Songti SC"）

### 基本使用流程

1. 克隆或下载此仓库到本地
2. 根据需求修改 `example.typ` 文件或创建新的 `.typ` 文件
3. 使用 Typst 编译生成 PDF 幻灯片

```bash
# 编译示例文件
typst compile example.typ
```

## 📝 基本用法

### 模板导入与基本设置

在你的 `.typ` 文件开头导入模板并设置基本信息：

```typst
#import "template/pku-template.typ": *

#show: doc => pku-theme(
  title: "演示文稿标题",
  subtitle: "演示文稿副标题",
  author: "作者姓名",
  institute: "所属院系\n北京大学",
  date: "2025年5月25日",
  doc,
)
```

### 创建幻灯片内容

模板使用 Typst 的标题系统来组织幻灯片内容：

- 一级标题 (`=`) 用于主要章节，会自动分页
- 二级标题 (`==`) 用于子章节，默认也会分页
- 可以使用 `#pku-enable-pagebreak(false)` 来控制是否分页

```typst
= 第一章节
#pku-enable-pagebreak(false) // 关闭自动分页
== 第一节

这是第一节的内容...

#pku-enable-pagebreak(true) // 开启自动分页
== 第二节

这是第二节的内容...
```

### 基本排版元素

模板提供了多种排版元素和样式：

- 文本样式：`#text(size: 20pt, fill: pku-red)[红色文本]`
- 列表：使用 Typst 标准列表语法，已设置北大红色项目符号
- 表格：使用 Typst 标准表格语法
- 图片：`#image("assets/images/example.png", width: 80%)`
- 公式：`$ E = m c^2 $`

## 🔍 高级功能

### 自定义文本块

模板提供了多种文本块样式：

```typst
// 标准文本块
#pku-block(title: "标题")[
  这是一个普通文本块内容
]

// 警告文本块（红色）
#pku-alert-block(title: "注意")[
  这是一个警告文本块内容
]
```

### 分栏布局

使用 `pku-columns` 函数创建分栏布局：

```typst
#pku-columns(
  60%, // 左侧列宽度
  [
    // 左侧内容
    *左侧内容 (60%)*
    - 左侧列表项
  ],
  [
    // 右侧内容
    *右侧内容 (40%)*
    1. 右侧数字列表
  ]
)
```

### 代码展示

展示代码块的两种方式：

```typst
// 方式一：直接使用 Typst 代码块
#block(
  fill: rgb(245, 245, 245),
  stroke: (left: 3pt + pku-blue),
  radius: 4pt,
  width: 100%,
  inset: 10pt,
  ```python
  def hello_pku():
      print("Hello, Peking University!")
```

)

// 方式二：使用模板提供的函数（如果模板中定义了该函数）
#pku-code("def hello_pku():\n    print('Hello, PKU!')", lang: "python")

```

### 手动分页控制

除了自动分页控制外，还可以使用手动分页：

```typst
// 手动强制分页
#pku-pagebreak()
```

## 🔧 自定义修改

### 修改主题颜色

模板定义了北大标准红蓝色：

```typst
// 在 template/pku-template.typ 中修改
#let pku-red = rgb(160, 0, 0)
#let pku-blue = rgb(0, 64, 152)
```

如需自定义，可以修改这些颜色定义。

### 修改字体

默认使用 "Songti SC" 作为中文字体，可以根据需要修改：

```typst
// 在 template/pku-template.typ 中找到并修改
set text(font: ("你想要的字体", "Songti SC"))
```

### 修改页面尺寸和边距

模板使用 4:3 的演示文稿比例，可以根据需要修改：

```typst
// 在 template/pku-template.typ 中找到并修改
set page(
  paper: "presentation-4-3", // 可以改为 "presentation-16-9"
  margin: (x: 1.5cm, y: 1.5cm),
  // ...其他设置
)
```

### 添加新的自定义函数

可以在 `template/pku-template.typ` 文件末尾添加新的函数，例如：

```typst
// 添加新的自定义函数
#let pku-highlight(body) = {
  text(fill: white, bg: pku-red, body)
}
```

## ❓ 常见问题

### 中文字体显示问题

如果中文显示不正确，请确保：

1. 系统安装了 "Songti SC" 字体，或修改模板中的字体设置为你系统可用的中文字体
2. 使用最新版本的 Typst 编译

### 图片路径问题

图片路径是相对于当前 `.typ` 文件的位置，建议将图片放在 `assets/images/` 目录下，并使用相对路径引用：

```typst
#image("assets/images/your-image.png", width: 80%)
```

### 自定义页眉页脚

模板中已设置页眉显示当前章节标题和校徽，页脚显示页码。如需修改，请查看 `template/pku-template.typ` 文件中的 `header` 和 `footer` 设置。

## 📄 许可证

本项目遵循开源许可证，欢迎使用和贡献。使用北京大学校徽时请遵守相关规定。

---

希望这个模板能够帮助您创建出专业、美观的北京大学演示文稿！如有问题或建议，欢迎提交 issue 或 pull request。
