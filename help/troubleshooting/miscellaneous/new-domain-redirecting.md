---
title: 新域正在重定向到默认域
description: 本文修复了新域重定向到现有或其他环境中的默认域的问题。
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 新域正在重定向到默认域

本文修复了新域重定向到现有或其他环境中的默认域的问题。

## 受影响的产品和版本

* Adobe Commerce on cloud pro基础架构（所有版本）

## 问题

新域正在重定向到当前环境中的默认域或其他环境的默认域。

## 原因

当添加新域后未更新变量或在环境中配置了错误的[!DNL Fastly]服务时，会发生这种情况。

## 解决方案

1. 如果域在同一环境中重定向，请确保已配置[变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables)。
1. 如果域正在重定向到其他环境，请运行以下命令检查是否已配置正确的[!DNL Fastly]服务： `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>通过登录到每个环境（暂存/生产）并检查`/mnt/shared/fastly_tokens.txt`文件，您可以找到[!DNL Fastly] API凭据。 有关详细信息，请参阅Commerce on Cloud Infrastructure指南中的[配置 [!DNL Fastly] 服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。

如果上述配置均正确，请提交支持工单。

## 相关阅读

* 在我们的支持知识库中设置[新域的清单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html)。
