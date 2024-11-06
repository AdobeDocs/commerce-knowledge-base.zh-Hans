---
title: 'MDVA-40550：重新索引后前端上缺少产品'
description: MDVA-40550修补程序解决了重新索引导致部分或所有店面类别缺少产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40550。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550：重新索引后前端上缺少产品

MDVA-40550修补程序解决了重新索引导致部分或所有店面类别缺少产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40550。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 创建产品。
1. 按计划&#x200B;**将索引器切换为**&#x200B;更新。
   * 将产品分配给类别。
1. 在`\Magento\Indexer\Model\Indexer::reindexAll`和`\Magento\Indexer\Model\IndexMutex::execute`中启用xdebug并生成xdebug断点。
1. 使用以下命令运行`catalog_category_product`的&#x200B;**完整重新索引**：

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * 等待在断点`\Magento\Indexer\Model\Indexer::reindexAll`上停止执行。

1. 在另一个控制台中，并行运行以下命令： **部分重新索引**

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 等待在断点`\Magento\Indexer\Model\IndexMutex::execute`上停止执行。 它将锁定`catalog_category_product`索引器。
1. 继续执行`catalog_category_product`的完整重新索引，并等待锁定超时（60秒）。

<u>预期的结果</u>：

控制台中没有错误消息。

<u>实际结果</u>：

您会收到以下错误：

*无法获取索引锁定： catalog_category_product。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
