---
title: 受限的管理员访问权限导致性能问题
description: 当使用我们用户指南中的[角色范围受网站限制的管理员角色](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)对性能产生负面影响时，本文提供了相应的解决方案。
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# 受限的管理员访问权限导致性能问题

本文提供了解决方案，用于解决在我们的用户指南中使用角色范围受网站[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)限制的管理员角色对性能产生负面影响的情况。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

当角色范围受网站限制的管理员用户在“管理员”面板中执行操作（包括登录、保存产品等）时，Adobe Commerce会重建存储的缓存。 重建缓存会对性能产生负面影响，并可能导致站点中断，尤其是在业务和/或高流量时段。

已在Adobe Commerce 2.2.10和2.3.3中修复此问题。

## 解决方案

以下是避免此问题的选项：

* 将Adobe Commerce应用程序版本升级到2.2.10或2.3.3。 (有关说明，请参阅我们的开发人员文档中的[在云基础架构上升级Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)。)
* 如果可能，请避免按网站限制管理员用户角色范围。
* [提交Magento支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以请求修补程序（如果可用）。

## 相关阅读

* 我们用户指南中的[用户角色](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)。
