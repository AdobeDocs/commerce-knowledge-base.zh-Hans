---
title: 适用于Adobe Commerce的升级兼容性工具1.1.0
description: 升级兼容性工具1.1.0是一个命令行工具，它通过分析安装在Adobe Commerce自定义实例中的所有模块和核心代码，根据特定版本检查该实例。 它会返回在升级到最新版本的Adobe Commerce之前必须解决的关键错误、问题和警告列表。
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# 适用于Adobe Commerce的升级兼容性工具1.1.0

升级兼容性工具1.1.0是一个命令行工具，它通过分析安装在Adobe Commerce自定义实例中的所有模块和核心代码，根据特定版本检查该实例。 它会返回在升级到最新版本的Adobe Commerce之前必须解决的关键错误、问题和警告列表。

## UCT 1.1.0有哪些新增功能？

升级兼容性工具1.1.0引入了显着改进，包括：

* **验证核心文件修改**：Adobe强烈建议不要自定义核心产品代码。 在此版本中，我们为客户和合作伙伴添加了一个检查点，用于识别对核心代码的任何修改，以尽早并快速了解修改的影响。 在开发过程中添加此工具将有助于合作伙伴和商户主动发现问题，防止未来升级期间出现问题，并降低总拥有成本(TCO)。
* **将报告导出到JSON文件**：此改进是在社区反馈后实施的。 现在，当您运行该工具时，所有已识别问题的详细信息都会导出到JSON文件，以便用户无需再次运行该工具即可读取、共享和管理结果。
* **已改进的VBE验证**： VBE（供应商捆绑的扩展）不是Adobe Commerce核心代码的一部分，但已通过Adobe测试并受其支持。 通过此更新，我们现在使用与核心代码相同的方法验证VBE。 这项改进将帮助用户清楚地了解与自定义和核心代码/VBE相关的问题。
* **提供错误代码**：我们引入了错误代码，以帮助用户识别、理解和解决升级期间的问题。 错误和警告消息提供清晰的描述和建议的解决方案。
* **可能仅列出关键问题**：这样，用户将能够仅关注那些关键问题，并在升级时生成问题。
* **两个版本之间的差异问题**：通过我们的社区成员提出的此改进，UCT用户将能够获取两个版本之间的差异问题，这将使他们能够仅关注针对要升级的目标版本引入的新问题。

## 该工具可以比较哪些版本？

您可以使用该工具来比较任何2.x版本。

## 谁可以使用升级兼容性工具1.1.0？

Adobe Commerce客户。

## 安装升级兼容性工具1.1.0

有关安装步骤，请参阅我们的开发人员文档中的Adobe Commerce： [升级兼容性工具>安装](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run)。 有关使用该工具的先决条件，请参阅我们的开发人员文档中的Adobe Commerce： [升级兼容性工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites)。

## 每个问题旁边的编号是多少？

这是错误消息引用，提供了有关执行升级兼容性工具时可能发生的错误的信息。

升级兼容性工具错误消息按级别（严重问题、错误和警告）和类型(核心代码、自定义代码和GraphQL架构)进行分类。 每种类型都包含以下信息：

* 错误代码：为错误消息分配的Adobe Commerce标识符。
* 错误描述：总结错误原因的描述。
* 错误建议操作：如果适用，为排除故障和解决错误提供指导。
* 在[错误消息引用页](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages)上列出并描述了代码。

## 可在何处分享关于该工具的反馈？

您可以联系我们[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) Slack频道上的UCT团队。 我们期待您提供反馈和改进该工具的建议。

## 相关阅读

* Adobe Commerce博客： [升级兼容性工具简介(Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce：在我们的开发人员文档中[升级兼容性工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview)。
