---
title: 冲突的组件依赖关系
description: 本文为组件依赖关系冲突提供了解决方案。 当尝试使用Web安装向导设置或更新Adobe Commerce时，您会看到*“我们发现了冲突的组件依赖项”*编辑器错误消息。
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 冲突的组件依赖关系

本文为组件依赖关系冲突提供了解决方案。 使用“Web设置向导”设置或更新Adobe Commerce时，您会看到 *“我们发现了冲突的组件依赖关系”* 编辑器错误消息。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x


## 问题 {#issue}

出现与以下内容类似的冲突组件依赖关系错误消息（实际的包名称和版本将有所不同）：

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## 原因

如果Composer无法确定要安装或更新哪些组件，则会显示此消息。

## 解决方案

两种主要情况可能会导致组件依赖关系发生冲突。 单击场景以获取故障排除步骤。

* [升级Adobe Commerce](#upgrading-magento)
* [与第三方模块不兼容：](#incompatibility-third-party-modules)
   * [Adobe Commerce（所有部署类型）](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## 升级Adobe Commerce {#upgrading-magento}

如果您在云基础架构上升级Adobe Commerce，请尝试以下操作以解决冲突的组件依赖关系：

* 检查用于升级的密钥。 密钥是否从正确的电子邮件帐户生成？
* 检查权限并确保它们与Magento升级要求匹配。 审核 [Magento升级概述>更新和升级核对清单>文件系统权限](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) 在我们的开发人员文档中。

## 与第三方模块不兼容： {#incompatibility-third-party-modules}

第三方模块依赖于比您安装的组件更早的Commerce组件，也可能会导致组件依赖关系冲突。 尝试以下操作：

1. 在前面 [示例](#issue)，则已安装的包magento/sample-data版本0.74.0-beta15无法升级到1.0.0-beta。 但是，0.74.0-beta15可以升级到0.74.0-beta16（或其他）。 编辑 `composer.json` 进行这些更改。 通常，您项目请求的版本将在 `require` 或 `require-dev` JSON文件中对象的属性。 根据提供的包版本选项，它们可以指定特定版本或约束。 有关如何使用编辑器的常规指导，如果您在我们的云基础架构上，可以参阅 [Cloud for Adobe Commerce >技术和要求>编辑器](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) 在我们的开发人员文档中。 如果您在Adobe Commerce内部部署，请参阅 [Adobe Commerce >安装指南>使用编辑器安装Adobe Commerce](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. 现在，尝试准备情况检查。 审核 [Adobe Commerce升级概述>运行模块管理器>步骤1准备情况检查](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) 在我们的开发人员文档中。
1. 如果准备情况检查失败，出现另一条组件依赖关系检查失败消息，则根据您是否正在使用，单击以下链接 [Adobe Commerce](#magento-commerce-magento-commerce-cloud) 或 [Magento Open Source](#opensource) 以获取进一步的故障诊断步骤。

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. 请联系扩展的开发人员，以便他们可以为您提供帮助。 您可以在从Commerce Marketplace上购买扩展的页面上找到他们的联系信息。 查找 **联系销售商** 按钮显示在右侧面板上。 所有Commerce开发人员在Marketplace上发布扩展时，都需要提供用户指南和安装指南。 您可以在登陆页面的右侧找到这两个页面。
1. 如果您没有在合理的时间内收到卖方的回复，请 [联系Marketplace支持](mailto:commercemarketplacesupport@adobe.com) 这样我们就可以提醒他们客户支持承诺。

## Magento Open Source {#opensource}

在以下位置请求帮助： [我们的主要论坛](https://community.magento.com/) 或 [联系Adobe Commerce合作伙伴](https://magento.com/find-a-partner) 有助于解决Open Source问题。
