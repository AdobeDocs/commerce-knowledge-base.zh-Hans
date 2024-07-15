---
title: 'MDVA-34023修补程序：“没有此类实体具有addressId”错误'
description: MDVA-34023修补程序解决了客户的Web浏览器上随机出现“没有此类具有addressId的实体”错误的问题。
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-34023修补程序：“没有此类实体具有addressId”错误

MDVA-34023修补程序解决了在客户的Web浏览器上随机发生`No such entity with addressId`错误的问题。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.1上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **设置** > **配置** > **客户选项卡** > **永久购物车**。
1. 设置&#x200B;**启用持久性** = *是*，设置&#x200B;**注销时清除持久性** = *否*。    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. 创建新客户，并定义默认发运地址和开单地址。
1. 注销。
1. 选中&#x200B;**记住我**&#x200B;复选框后登录。
1. 转到`customer_entity`数据库表并将`default_billing`和`default_shipping` ID更改为非现有ID。
1. 注销。

<u>预期的结果</u>：

没有出现预期错误。

<u>实际结果</u>：

将生成异常日志：

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
