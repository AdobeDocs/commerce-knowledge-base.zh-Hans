---
title: 未知模块MagentoBundleSampleData
description: 本文修复了安装Adobe Commerce期间出现的未知模块错误。
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# 未知模块MagentoBundleSampleData

本文修复了安装Adobe Commerce期间出现的未知模块错误。

## 问题 {#details}

在安装过程中，会显示与以下内容类似的消息：

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## 解决方案 {#solution}

请逐一尝试以下各项，然后再次尝试安装。

1. 运行Web安装向导。 中列出了模块  **高级模块配置**. 要禁用 **Magento\_BundleSampleData** 模块，清除 **Magento\_BundleSampleData** 复选框，下图所示。

   ![tshoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. 清除Web浏览器中的所有浏览器历史记录和数据。
1. 如果您使用的是Chrome，请清除与您的网站相关的所有浏览器数据。  转到 **设置** > **高级选项** > **隐私** > **内容设置** > **所有Cookie和网站数据**. 在站点列中，单击Adobe Commerce服务器的地址，然后单击 **全部删除**.
