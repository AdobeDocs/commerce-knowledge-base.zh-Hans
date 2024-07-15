---
title: Google Analytics未跟踪转化数据
description: 针对与Google Analytics不跟踪转化数据相关的已知Adobe Commerce 2.2.4问题，本文提供了一个修补程序。
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics未跟踪转化数据

针对与Google Analytics不跟踪转化数据相关的已知Adobe Commerce 2.2.4问题，本文提供了一个修补程序。

>[!NOTE]
>
>已在Adobe Commerce 2.2.6中修复此问题。

## 问题

由于Google Analytics组件代码中有错误，Google Analytics未跟踪转化数据。

<u>重现步骤</u>：

1. 在Commerce管理员的&#x200B;**商店** > **设置** > **配置** > **销售** > **Google API** > **Google Analytics**&#x200B;下启用和配置Google Analytics功能。
1. 单击&#x200B;**保存配置**。
1. 在店面下订单。
1. 转到&#x200B;**Google Analytics信息板** > **转化** > **概述**。
1. 将日期范围设置为当前日期。

<u>预期的结果</u>：

转换数据中将显示顺序。

<u>实际结果</u>：

该顺序不会出现在转化数据中。

## 解决方案

该修补程序修复了Google Analytics组件代码中的错误。 应用修补程序后，Google Analytics将跟踪修补程序转换数据。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-11263\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce内部部署2.2.4

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.2.5
* 云基础架构上的Adobe Commerce 2.2.4、2.2.5

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
