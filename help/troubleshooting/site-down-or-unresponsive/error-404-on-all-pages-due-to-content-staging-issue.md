---
title: 由于内容暂存问题，所有页面均显示错误404
description: 本文修复了Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure问题，该问题导致您在访问任何店面页面或[!UICONTROL Commerce Admin]时出现404错误。
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 由于内容暂存问题，所有页面均显示错误404

本文修复了Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure问题，该问题导致您在访问任何店面页面或[!UICONTROL Commerce Admin]时出现404错误。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

>[!NOTE]
>
>本文不适用于尝试[预览暂存更新](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change)时出现404错误的情况。 如果您遇到此问题，请打开[支持票证](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)。

访问任何店面页面或管理员会导致404错误（“糟糕，我们的错误……”页面），原因是使用[内容暂存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=zh-Hans)对商店内容资源执行计划更新操作后(对使用[Magento\_暂存模块](https://developer.adobe.com/commerce/php/module-reference/)计划的商店内容资源的更新)。 例如，您可能已删除了计划更新的产品，或删除了计划更新的结束日期。

商店内容资产包括：

* 产品
* 类别
* 目录价格规则
* 购物车价格规则
* CMS页面
* CMS块
* 构件

下面的“原因”一节将讨论一些情形。

## 原因

数据库(DB)中的`flag`表包含指向`staging_update`表的无效链接。

该问题与内容暂存相关。 以下是两种特定情况；请注意，可能有更多情况会触发该问题。

**方案1：**&#x200B;正在删除商店内容资源，该资源：

* 已计划内容暂存的更新
* 更新具有结束日期（即更新的资产恢复到其先前版本的到期日期）
* 更新的结束日期是过去的时间

同时，如果删除的资产没有计划更新的结束日期，则可能不会发生问题。

**方案2：**&#x200B;正在删除计划更新的结束日期/时间。

### 确定您的问题是否相关

要确定您遇到的问题是否为本文所述的问题，请运行以下数据库查询：

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

如果查询返回的`update_exists`值为“0”的表，则数据库中存在指向`staging_update`表的无效链接，并且[解决方案部分](#solution)中描述的步骤将有助于解决此问题。 以下是`update_exists`值等于“0”的查询结果示例：

![update_exists_0.png](assets/update_exists_0.png)

如果查询返回的`update_exists`值为“1”的表或结果为空，则表示您的问题与暂存更新无关。 以下是`update_exists`值等于“1”的查询结果示例：

![updates_exist_1.png](assets/updates_exist_1.png)

在这种情况下，您可以参阅[Site Down Troubleshooter](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter)以了解故障排除想法。

## 解决方案

1. 运行以下查询以删除指向`staging_update`表的无效链接：

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. 等待[!DNL cron]作业运行（如果设置正确，最多可在五分钟内运行）；如果未设置[!DNL cron]，请手动运行该作业。

该问题应在修复无效链接后立即解决。 如果问题仍然存在，请[提交支持票证](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)。

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
