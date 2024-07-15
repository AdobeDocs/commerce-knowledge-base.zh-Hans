---
title: 'MDVA-29389：高级报告相关cron作业失败'
description: “MDVA-29389修补程序修复了高级报表中存在的一个问题，即“analytics_collect_data”cronjob指示：“*Port必须在主机参数（如localhost：3306）*”中进行配置。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 修补程序ID为MDVA-29389。 已在Adobe Commerce 2.4.2中修复此问题。'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389：高级报告相关cron作业失败

MDVA-29389修补程序修复了高级报告的问题，该问题导致`analytics_collect_data` cronjob显示： “*Port必须在主机参数（如localhost：3306）*”中进行配置。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 修补程序ID为MDVA-29389。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法）2.3.4。

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.0 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 在Adobe Commerce实例中，启用高级报告。
1. 运行以下查询以在数据库中插入analytics/general/token值：

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. 打开您的env.php并按以下格式在数据库配置中将端口添加到主机参数： `'host' => 'hostname:port',`
1. 清除缓存。
1. 执行`analytics_collect_data` cron作业。

<u>预期的结果</u>：

使用默认或非默认端口连接到env.php中的MySQL时，`analytics_collect_data`作业成功运行。

<u>实际结果</u>：

在env.php中使用非默认端口连接到MySQL时，`analytics_collect_data`作业引发错误“*端口必须在主机参数（如localhost：3306）*”中进行配置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
