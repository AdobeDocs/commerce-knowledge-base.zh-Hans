---
title: 删除暂存更新将删除相关实体
description: 本文为与实体相关的已知Adobe Commerce 2.2.3问题（类别、CMS页面等）提供了一个修补程序 本身将在删除相关计划更新时被删除。
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 删除暂存更新将删除相关实体

本文为与实体相关的已知Adobe Commerce 2.2.3问题（类别、CMS页面等）提供了一个修补程序 本身将在删除相关计划更新时被删除。

>[!NOTE]
>
>已在Adobe Commerce 2.2.6中修复此问题。

## 问题

删除开始日期和结束日期之间的活动计划更新时，也会删除相关实体（类别、子类别、CMS页面）。

<u>要再现的步骤（使用类别）</u>：

1. 登录到Commerce管理员。
1. 在&#x200B;**目录** > **类别**&#x200B;下创建新子类别。
1. 使用开始和结束时间创建新的暂存更新。
1. 等待应用更新；即开始时间。
1. 使用&#x200B;**查看/编辑**&#x200B;链接删除更新。

<u>预期的结果</u>：

更新已删除，并且子类别仍然存在于管理员中。

<u>实际结果</u>：

将删除更新和子类别。

## 解决方案

请应用本文中提供的修补程序，并清除正在运行的缓存

```bash
bin/magento
  cache:clean
```

## Patch

修补程序已附加到本文。 要下载补丁程序，请向下滚动到文章末尾，然后单击文件名或单击相应的链接：

* [下载MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [下载MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [下载MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### 兼容的Adobe Commerce版本：

修补程序是为以下对象创建的：

* 已为Adobe Commerce（所有部署方法）2.2.3创建MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch
* 已为Adobe Commerce（所有部署方法）2.2.4创建MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch
* 已为Adobe Commerce（所有部署方法）2.2.5创建MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch

MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch修补程序与以下Adobe Commerce版本兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.2.0 - 2.2.2
* 云基础架构上的Adobe Commerce 2.2.0 - 2.2.3

MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch修补程序与以下Adobe Commerce版本兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.1.0 - 2.1.18、2.2.0 - 2.2.3
* 云基础架构上的Adobe Commerce 2.1.0 - 2.1.18、2.2.0 - 2.2.3

MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch修补程序与以下Adobe Commerce版本兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.2.5

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
