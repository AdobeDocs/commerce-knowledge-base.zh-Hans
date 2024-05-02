---
title: 'MDVA-23764Magento修补程序：加载动态块时出错'
description: MDVA-23764Magento修补程序修复了中的错误
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764Magento修补程序：加载动态块时出错

MDVA-23764Magento修补程序修复了中的错误

```php
JsFooterPlugin.php
```

这会影响动态块的显示。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.13。 请注意，已在Magento2.3.5中修复此问题。

## 受影响的产品和版本

**该修补程序是为Magento版本创建的：** Magento Commerce Cloud2.3.3。

**与Magento版本兼容：** Magento Commerce和Magento Commerce Cloud2.3.2 - 2.3.4-p2。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤：</u>

尝试加载如下所示的URL： https://\[magento domain\]/banner/ajax/load/。

<u>实际结果：</u>

引发与以下内容类似的错误： *未捕获的TypeError： strpos()要求参数1为字符串，null以……（代码行）指定* .

<u>预期结果：</u>

加载的URL没有出现错误。

## 应用修补程序

有关如何应用QPT补丁程序的说明，请根据您的Magento产品使用以下链接：

* Magento Commerce： DevDocs [使用Quality Patches工具应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud： DevDocs [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [使用Quality Patches Tool检查是否有可用于Magento问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
