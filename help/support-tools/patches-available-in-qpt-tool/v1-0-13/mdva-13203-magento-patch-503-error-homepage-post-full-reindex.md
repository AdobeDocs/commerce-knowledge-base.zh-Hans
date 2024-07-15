---
title: 'MDVA-13203修补程序：发布完全重新索引后出现503错误主页'
description: “MDVA-13203 Adobe Commerce修补程序修复了以下问题：您的站点显示维护页面，并且“system.log”中存在*CRITICAL： SQLSTATE\[23000\]：完整性约束冲突*错误。” 修补程序ID为MDVA-13203。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203修补程序：发布完整重新索引后出现503错误主页

MDVA-13203 Adobe Commerce修补程序修复了以下问题：您的站点显示维护页面，且`system.log`中存在&#x200B;*CRITICAL： SQLSTATE\[23000\]：完整性约束冲突*&#x200B;错误。 修补程序ID为MDVA-13203。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。

## 受影响的产品和版本

**在Cloud Infrastructure 2.2.4上为Adobe Commerce版本** Adobe Commerce创建修补程序。

**与Adobe Commerce版本兼容：** Adobe Commerce（所有部署方法） 2.3.0-2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>要再现的步骤：</u>

1. 转到受影响的URL。
1. 您会看到维护页面。
1. 通过SSH检查站点是否处于维护状态：
   <pre> bin/magento维护：状态
    状态：维护模式未处于活动状态
    免除IP地址列表：无</pre>
1. 查看`system.log`：

<pre>grep critical -i var/log/system.log |尾

[2018-09-04 17:05:18] report.CRITICAL： SQLSTATE[23000]：完整性约束违规：1062键“PRIMARY”的重复条目“4613”，查询为：INSERT INTO 'search_tmp_5b8ebb4e994da5_88027289' ('entity_id'，'score')值(？， ？)，.. (？， ？)， (？， ？) [] []
[2018-09-04 17:05:21] report.CRITICAL： SQLSTATE[23000]：完整性约束违规：1062键“PRIMARY”的重复条目“4613”，查询为：INSERT INTO 'search_tmp_5b8ebb51579943_52333638' ('entity_id'，'score')值(？， ？)，..，(？) [] []
[2018-09-04 17:05:47] report.CRITICAL： SQLSTATE[23000]：完整性约束违规： 1062键“PRIMARY”的重复条目“1350”，查询为： INSERT INTO 'search_tmp_5b8ebb6b7028f4_68065024' ('entity_id'，'score')值(？、？)、(？、？)、(？、？)、(？)、(？)、(？ ？？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？) [] []
[2018-09-04 17:05:47] report.CRITICAL： SQLSTATE[23000]：完整性约束违规： 1062键“PRIMARY”的重复条目“1350”，查询为： INSERT INTO 'search_tmp_5b8ebb6b7885a9_23360993' ('entity_id'，'score')值(？、？)、(？、？)、(？)、(？)、(？)、(？ ？？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？) [] []

日期

2018年9月4日星期二17:06:11 UTC</pre>

<u>预期结果：</u>您应该会看到网站。

<u>实际结果：</u>由于数据库一致性问题，显示维护页。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
