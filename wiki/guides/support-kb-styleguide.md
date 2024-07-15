---
source-git-commit: c992521cae8c847adc0cc23d2323300e0ba69cdc
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---
# 支持KB样式指南

在向Adobe Commerce帮助中心贡献内容时，请遵循这些风格和格式建议。

## 标题

* 标题采用句子式大写。
* 标题为复数；过程标题为单数。 示例： Title — 正在编写书籍。 标题 — 写一本书。
* 保持标题简短，在开头写上重要词语。 出于SEO原因，强烈建议标题长度不超过70个字符（标题减少会阻止传达真实含义的情况除外）。 

## 标头

* 顶层标题为H2。 （默认情况下，H1是文章标题，即使标题没有明显使用H1格式也是如此）。
* 对任务标题使用无限动词。 例如“如何识别高流量事件”。
* 任务标题使用单数形式。 例如，“模块结构”。
* 避免使用双标题（标题之间应至少包含一个句子）。
* 所有标题的句子式大写。
* 任务标题是必要的（“创建x”，而不是“创建x”或“创建x”）。

## 列表

* 任务中的步骤：最多9个

* 项目符号列表使扫描更容易。

   * 使用项目符号列表列出方法、方法、选项和非连续的任务步骤。
   * 用项目符号缩短文本，最好不超过两句话。
   * 尽可能减少子弹数量；最好是7发子弹或更少。
   * 避免在项目符号项目之间放置提示或注释。
   * 在列表中使用并行语法结构，但如果它导致过多的谓词或固定语言，则违反此规则。
   * 项目符号列表中每个项目的第一个单词使用大写，即使它是片段也是如此。

* 使您的列表平行。 例如，每个项目应该是一个名词或以动词开头的短语。

## 注释和提示

将注释和提示仅保留在一个段落中。 需要不止一款，就意味着需要调整内容并将其纳入本文。

## 大写

如有疑问，请勿使用大写。 在标题中，使用句子式大写。 专有名词和冒号后的第一个单词使用大写。

## UI元素

* 用户单击的所有内容都放入&#x200B;**bold**。 例如，“单击&#x200B;**继续**。” 选项值和错误消息的格式为&#x200B;_斜体_。
* 请尽量避免在说明中提及UI元素类型。 (单击&#x200B;**下一步**。 vs单击&#x200B;**下一步**&#x200B;按钮。)
* 在命令序列中使用“选择”和“>”。 (选择&#x200B;**编辑** > **首选项**。 与单击编辑 | 首选项。)
* 前置词：“在”用于对话框、窗口，包括面板、视图、向导、列表、文件夹和节点。
* 前置位置：屏幕、页面、工具栏、菜单栏、选项卡、窗格、功能区的“开”。
* 前置词：单击（单击&#x200B;**下一步**&#x200B;与单击&#x200B;**下一步**）。

## 文件名

文件名和文件夹的格式为代码。 示例： `/var/log`系统目录包含所有环境的日志。


## 数字

最重要的是，处理写出数字与数字问题时的一致性规则。

拼出数字，如“5”或“9”（当数字小于10时，即为1到9）。

在下列情况下用数字表示数字，如“42”或“11”：

* 数字超过9（数字为十或更大）。
* 您正在指定编号：
   * 在一行代码或代码片段中。
   * 在文件路径或目录名称内。
   * 在传达范围（如“5到25”或“审阅编号8到21”）时。
   * 这些数字是按照“62派卡”或“830 MHz”之类的标准来测量或计算的。

在注意一些具有编号的事物（如“一组15 1000次试用的运行”）时，使用数字组合。

如果句子中有两个数字，一个小于10（如4），一个大于10（如14），则用文字或数字同时写两个数字。 例如，您可以保留以下数字：“每4升液体留下14分钟”。


## 特定用语案例

<table class="relative-table" style="width: 100.0%;"><colgroup><col style="width: 12.003596%;"> <col style="width: 16.444849%;"> <col style="width: 71.55351%;"></colgroup>

<tbody>

<tr>

<th>不正确</th>

<th>正确</th>

<th> 推理
</th>

</tr>

<tr>

<td>登录到Magento.com帐户页面 </td>

<td>登录到您的Adobe Commerce帐户</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>第三方扩展（模块）</td>

<td>第三方扩展（模块）</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>SQL代码段</td>

<td>语句为大写（SELECT与SELECT）</td>

<td colspan="1">更好的可读性</td>

</tr>

<tr>

<td colspan="1">

对其他资源的引用。

示例：请参阅我们的开发人员文档上的xyz


</td>

<td colspan="1">请参阅我们的开发人员文档中的xyz</td>

<td colspan="1">

辅助功能要求：所有链接都描述链接的目标。


</td>

</tr>

<tr>

<td colspan="1">

Adobe Commerce v2.4.0

Adobe Commerce 2.4.0

Adobe Commerce版本2.4.0

</td>

<td colspan="1">Adobe Commerce 2.4.0（无版本或版本）</td>

<td colspan="1"></td>

</tr>

<tr>

<td colspan="1">

2.4.x

2.4.X

</td>

<td colspan="1">

2.4.0

2.4.x

</td>

<td colspan="1">

没有大写的理由。

</td>

</tr>

<tr>

<td colspan="1">

错误消息： _“出现错误。”_

错误消息： __发生错误。__

</td>

<td colspan="1"> 错误消息： <i>发生错误。</i> </td>

<td colspan="1">
</td>

</tr>

</tbody>

</table>

## 辅助功能

* 所有非文本或图形元素都具有文本等效项或替换文本。 示例：![example_image](/url "alt_text_for_this_image")。

* 所有链接都描述链接的目标。 示例[链接](/uri "destination_of_the_link")。


<!--
## Accessible tables

Use tables for information that is best presented along two axes (rows and columns). Do not use tables when a list or definition list serves the purpose. If using tables, follow these recommendations:

*   Headers for rows and columns; row headers easier for screen readers.

*   Simple linear construction.

*   Content within cells consistently structured.  -->


## 辱骂性语言

* 避免粗暴的语言。 
* 避免使用种族主义或“可能感觉像种族主义”的语言。
* 避免使用具有强烈负面含义或强烈情感色彩的语言，如“杀戮”、“终止”。


## 链接 

大多数链接都显示在文章内的链接列表中。 避免不必要的内联链接。

最佳做法是使用可配置的标题隔离链接列表中的内联链接。

专用链接列表（称为另请参阅列表）仅在文章末尾显示。    从战略角度使用链接列表，不过需要这样做。 根据经验，链接列表中的链接不得超过6个。

### 指向外部网站的链接

使用普通URL而不是goURL链接到[Adobe.com](http://Adobe.com)之外的页面。


## 逗号

通常，请遵循《芝加哥风格手册》的开放样式标点符号建议，仅在必要时使用标点符号以防止误读。 例如，如果复合句子的连接前省略逗号，几乎不会出现误读风险。 在需要澄清时请使用逗号。

* 在包含三个或更多项的列表中，始终使用串行逗号（位于&#x200B;_和_&#x200B;或&#x200B;_或_&#x200B;之前的逗号）： x、y和z

* 将逗号放在引入独立子句的结合项之前：“指定位置，并键入文件列表的名称。”

* 不要用逗号分隔平台差异：“…… Ctrl (Windows)或Command (Mac OS)”

* 在引言短语或子句之后始终使用逗号：“在Photoshop中，导入Illustrator文件。”

## 版本

* 我们会对所有发行版本（主要/次要/修补程序）使用“版本”。 例如“支持的版本：Adobe Commerce 2.3.x”

* 在编写有关次要版本中的所有修补程序版本以及所有包含主要修补程序的次要版本时，我们使用小写“x”。 例如，Adobe Commerce 2.x.x。

## 品牌化

* Magento Commerce现在是Adobe Commerce。 有关如何使用最新品牌语言的详细信息，请参阅[品牌推广术语](https://github.com/magento/knowledge-base/wiki) Wiki。
