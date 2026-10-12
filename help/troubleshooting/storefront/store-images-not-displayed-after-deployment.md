---
title: 部署后不显示存储映像
description: 本文为部署后图像无法正确显示提供了一个解决方案。
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# 部署后不显示存储映像

本文为部署后图像无法正确显示提供了一个解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

在调整图像大小时使用店面主题时，图像在部署时不会显示或从目录页面中消失。

## 原因

这可能是由于从缓存加载图像而发生的。

## 解决方案

如果发生这种情况，您可以使用Magento命令重新生成图像缓存并正确显示图像。

要执行此操作，您需要通过[云控制台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hans)提供的SSH信息和商店URL。

1. SSH到[数据库转储](/help/how-to/general/create-database-dump-on-cloud.md)的源项目，如开发人员文档中的[SSH到环境](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/secure-connections)中所述。
1. 通过运行以下代码重新生成图像缓存：

   ```bash
   php bin/magento catalog:images:resize
   ```

1. 通过商店URL测试类别页面。
