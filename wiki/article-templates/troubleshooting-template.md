---
title: '...'
labels: troubleshooting,...
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# 疑难解答文章模板

标题应简要描述问题，最好不超过70个字符。<br/>
（例如：“安装或升级期间出现内存不足错误”。）

有关元数据的更多信息，请参阅[参与>元数据](../../CONTRIBUTING.md#metadata)。

介绍一两个段落：问题的简要概述。 前140个字符对于SEO很重要。

## 受影响的产品和版本

* Adobe Commerce内部部署x.x.x
* 云基础架构x.x.x上的Adobe Commerce

（*如果云或本地的相同版本受到影响，您可以说：*）

Adobe Commerce（所有部署方法）x.x.x

* 受影响的扩展或技术（例如Redis、Fastly）：x.x.x

## 问题

对问题的清楚描述，包括完整的错误消息作为文本以及任何重要的屏幕截图。
如果在日志中找到此日志，请提供详细信息：哪个日志、位置。

从错误和日志中删除任何特定项目ID或客户信息！ 另外，请确保屏幕截图中未包含敏感信息。

如果在非常特定的情况下发生问题，请按照以下格式提供详细的步骤来重现问题、预期结果和实际结果：

<u>重现步骤</u>：

先决条件： ... （如果有）。

1. 第一步。
1. 第二步。
1. ....

<u>预期的结果</u>：

Adobe Commerce会这样做。

<u>实际结果</u>：

Adobe Commerce就是这么做的。

## 原因

出现问题的原因。 不要描述修复 — 它应该位于下一部分。 如果原因不明确或在此情况下不重要，请跳过此选项。

## 解决方案

如何修复此问题。 步骤使用编号列表。
完成该部分并返回结果：未显示错误、部署工作、值已更改以及如何查看更改等。

如果有临时解决方法，请将其指定为此解决方法下的单独部分。

## 相关阅读

* 我们用户指南中的[文章主题](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/user-guides/home)。
* 我们的开发人员文档中的[文章主题](https://developer.adobe.com/commerce/docs/)。 您还可以说要区分面向云用户和本地用户的devdocs中的说明：“[文章主题](https://developer.adobe.com/commerce/docs/)(在面向云基础架构的Adobe Commerce的开发人员文档中)”。 与“[文章主题](https://developer.adobe.com/commerce/docs/)”(在Adobe Commerce内部部署的开发人员文档中)。
* 我们的支持知识库中的[文章主题](https://support.magento.com/hc/en-us)。
* 任何相关资源（博客、论坛、StackOverflow等）
