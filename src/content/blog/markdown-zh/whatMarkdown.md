---
title: 我的Blog支持什么Markdown语法？
publishDate: 2025-07-27 15:36:51
description: 测试ing
tags:
  - Blog
  - Markdown
heroImage:
  src: ./1.jpg
  color: "#B4C6DA"
language: 中文
---
## Admonitions 警示块
警示框，又称提示框，是一种非常适合在不中断文档流的情况下包含附加内容的工具。Material for MkDocs 提供了多种类型的警示框，并允许在其中嵌套任意内容。
### 使用方法
警示框使用简单的语法：块以 !!! 开始，后跟一个作为类型限定符的关键字。块内容紧接在下一行，并缩进四个空格。
```Markdown
!!! note

    这是没有设置标题的 note 类型警示块。
```

!!! note

    这是没有设置标题的 note 类型警示块。


    
### 修改标题
在默认情况下，标题会显示为警示框的类型。但你可以通过在类型限定符后添加带引号的字符串来修改标题(支持有效的 Markdown 语法，包括链接、格式化等)。
```Markdown
!!! note "这里是[标题](#)"

    这是设置了标题的 note 类型警示块，
    你可以在标题里任意发挥，例如加一个超链接等。
```
!!! note "这里是[标题](#)"

    这是设置了标题的 note 类型警示块，
    你可以在标题里任意发挥，例如加一个超链接等。
### 支持的类型
Material for MkDocs 提供了以下类型的警示框：

!!! note
    这是 note 类型的警示框。

!!! tip
    这是 tip 类型的警示框。
    
!!! warning
    这是 warning 类型的警示框。

!!! danger
    这是 danger 类型的警示框。

!!! abstract
    这是 abstract 类型的警示框。

!!! info
    这是 info 类型的警示框。

!!! quote
    这是 quote 类型的警示框。

!!! warning
    这是 warning 类型的警示框。

!!! bug
    这是 bug 类型的警示框。


!!! fail
    这是 fail 类型的警示框。


!!! question
    这是 question 类型的警示框。

!!! success
    这是 success 类型的警示框。

<https://github.com/saicaca/fuwari/>

