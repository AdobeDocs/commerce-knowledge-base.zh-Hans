---
title: '部署失败：无法应用MDVA-43395修补程序'
description: 本文提供了针对此问题的解决方案，其中尝试应用MDVA-43395修补程序会导致部署失败。
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 部署失败：无法应用MDVA-43395修补程序

本文提供了针对此问题的解决方案，其中尝试应用MDVA-43395修补程序会导致部署失败。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本）

## 问题

无法应用MDVA-43395修补程序。

## 原因

如果云商已安装[magento/magento-cloud-patches 1.0.16](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016)，并且其中已包含修补程序，则无需单独应用MDVA-43395修补程序。

## 解决方案

要解决此问题，请从`m2-hotfixes`目录中删除MDVA-43395和MDVA-43443修补程序并重新部署。

如果可以通过`m2-hotfixes`目录应用MDVA-43443修补程序，则仍需要按上述方式将其删除。 Adobe Commerce的未来版本中将已包含这些修补程序，因此如果您稍后升级，可能会导致部署失败。

要验证是否已应用修补程序，请运行`vendor/bin/magento-patches -n status |grep 43443`命令。
如果它显示多个类似这样的结果，则应从`m2-hotfixes`文件夹中删除MDVA-43443修补程序：

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## 相关阅读

* [如何应用我们的支持知识库中Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
* 在开发人员文档中[Commerce的云修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016)。
