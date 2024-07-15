---
title: 运行setup：upgrade时出现“区码未设置”错误”
description: 本文为云基础架构2.2.3上的已知Adobe Commerce提供一个修补程序，该问题与运行setup：upgrade命令时出现*未设置区码*错误相关。
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 运行`setup:upgrade`时出现“未设置区号”错误

本文为云基础架构2.2.3上已知的Adobe Commerce问题提供了一个修补程序，该问题与运行以下命令时出现&#x200B;*“未设置区码”*&#x200B;错误有关：

```bash
setup:upgrade
```

>[!NOTE]
>
>已在Adobe Commerce 2.2.4中修复此问题。

## 问题

运行时

```bash
bin/magento setup:upgrade
```

命令，您会收到以下错误消息： *&quot;Module &#39;Magento\_AdvancedSalesRule&#39;：正在安装数据……未设置区号：在启动会话之前必须设置区号&quot;*，命令执行已中断。 出现此问题是因为在实际设置区域配置之前请求了区域配置。 该修补程序允许捕获错误，并且不会中断升级过程。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.3

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.2.0 - 2.2.3

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
