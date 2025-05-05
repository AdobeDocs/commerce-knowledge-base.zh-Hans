---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# 知识库格式化指南

## Markdown中的作者

我们通常使用[Adobe Experience League Markdown语法样式指南](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=zh-Hans)，但存在一些差异和异常。 此外，在某些情况下，还需要使用某些HTML标签。

以下是存储库中最常用的Markdown格式示例。

## 基本格式

要将文本格式设置为粗体，请用两个星号将文本括起来：

`This will be **bold** text`

要将文本格式设置为斜体，请使用单星号：

`This text will be *italics*`

要将文本格式设置为下划线，请使用`<ins>`标记：

`<ins>This text will be underlined</ins>`

要添加换行符，请使用`<br>`HTML标记。


## 标头

对从H2到H5的标题使用以下格式。 从不会使用H1，因为文章标题会视为H1。

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## 代码内嵌和块

使用单个反撇号将要高亮显示的代码元素括起来：

这是文本段落中的\“内联代码\”。

### 代码块

要插入一个代码块，请用三个反撇号将代码块括起来，并在打开三个反撇号后指定语言：

\`\`\` sql

选择TABLE_NAME作为`Table`，
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024)作为`Size (MB)`
FROM information_schema.TABLES
其中TABLE_SCHEMA =“%project_id%”
排序依据(DATA_LENGTH + INDEX_LENGTH)说明；

\`\`\`

这将呈现为：

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

根据我们的筛选规则，您始终需要为代码块指定语言。

有关支持的语言列表，请查看https://github.com/github/linguist/blob/master/lib/linguist/languages.yml。

如果突出显示对于Markdown中的特定语言不起作用（即不支持该语言），则要使其在发布到https://support.magento.com/hc/en-us/时至少突出显示，请使用以下HTML：

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

其中``%language-code%``是由[Prism.js支持的语言](https://prismjs.com/#supported-languages)定义的代码。

## 列表

列表总是与其他内容以空白行分隔。 列表前后应显示一行空白。

对排序列表使用以下格式：

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

要创建无序项目符号列表，请在行首使用*、+或 — 。 但请选择一种方法，并在整篇文章中始终如一地使用它。

示例：

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

要在列表项之间添加内容，请在行的开头添加4个空格：

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

您也可以通过此方式嵌入列表。

## 链接

外部链接非常直接：

```markdown
[Adobe](https://www.adobe.com)
```

### 指向附件的链接

任何类型的附件都应采用.png、.jpg和.jpeg格式。 为安全起见，我们仅接受采用三种格式之一的附件。

要插入图像，请将图像放置在与文章相同的节文件夹中的&#x200B;*assets*&#x200B;子文件夹中，并使用以下语法将图像插入文章：

```markdown
![alt text](assets/image.png)
```

如果要自定义图像的大小，需要使用以下HTML标记进行自定义：

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### 指向文章中特定部分的链接

如果需要引用文章中的某个章节，则无需创建单独的锚点。 所有H2-H6标题的锚点会在发布时自动生成。 锚点是从标题生成的，方法是将所有单词变为小写并使用“ — ”分隔单词。

示例：

```markdown
## This is header
```

这是指向以下标题的链接：

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

如果需要引用标头以外的元素，请使用HTML来定义要添加元素，并使用[id属性](https://www.w3schools.com/html/html_id.asp)。 然后，您可以使用Markdown或HTML引用此ID。

### 其他文章的相对链接和链接

请勿使用相对链接来引用我们的支持知识库文章。 当您的文章在[Adobe Commerce帮助中心](https://support.magento.com/hc/en-us)中发布时，这些链接将不起作用。
请使用[Adobe Commerce帮助中心](https://support.magento.com/hc/en-us)中的完整超链接。


## 表

对表[&#128279;](https://www.w3schools.com/html/html_tables.asp)使用HTML格式。


## 警告和信息块

成功注释块：

```
>![success]
>
>This is a success note
```

警告块：

```
>![warning]
>
>This is a warning
```

信息注释块：

```
>![info]
>
>This is a block with additional info
```
