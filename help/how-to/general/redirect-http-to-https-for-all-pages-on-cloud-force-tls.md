---
title: 对于云基础架构上的Adobe Commerce上的所有页面，将HTTP重定向到HTTPS（强制TLS）
description: 在Commerce管理员中激活Fastly的**强制TLS**功能，以便为云基础架构存储上的Adobe Commerce的所有页面启用全局HTTP到HTTPS重定向。
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 对于云基础架构上的Adobe Commerce上的所有页面，将HTTP重定向到HTTPS（强制TLS）

在Commerce管理员中激活Fastly的&#x200B;**强制TLS**&#x200B;功能，以便为云基础架构存储上的Adobe Commerce的所有页面启用全局HTTP到HTTPS重定向。

本文提供了详细的[步骤](#steps)、强制TLS功能的快速概述、受影响的版本以及指向相关文档的链接。

## 步骤 {#steps}

### 步骤1：配置安全URL {#step-1-configure-secure-urls}

在此步骤中，我们为存储定义安全URL。 如果已经这样做，请转到[步骤2：启用强制TLS](#step-2-enable-force-tls)。

1. 登录到Commerce管理员。
1. 导航到&#x200B;**商店** > **配置** > **常规** > **Web**。
1. 展开&#x200B;**基本URL （安全）**&#x200B;部分。    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. 在&#x200B;**安全基础URL**&#x200B;字段中，指定存储的HTTPS URL。
1. 将&#x200B;**在店面上使用安全URL**&#x200B;和&#x200B;**在管理员上使用安全URL**&#x200B;设置设置为&#x200B;**是**。    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. 单击右上角的&#x200B;**保存配置**&#x200B;以应用更改。

用户指南中的&#x200B;**相关文档：**   [存储URL](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls)。

### 步骤2：启用强制TLS {#step-2-enable-force-tls}

1. 在Commerce管理员中，导航到&#x200B;**商店** > **配置** > **高级** > **系统**。
1. 展开&#x200B;**全页缓存**&#x200B;部分，然后展开&#x200B;**快速配置**，最后展开&#x200B;**高级配置**。
1. 单击&#x200B;**强制TLS**&#x200B;按钮。    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. 在出现的对话框中，单击&#x200B;**上传**。    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. 对话框关闭后，确保强制TLS的当前状态显示为&#x200B;**已启用**。    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**相关Fastly文档：**   适用于Adobe Commerce 2的[强制TLS指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)。

## 关于强制TLS

TLS（传输层安全性）是一种用于安全HTTP连接的协议，它取代了其不太安全的前置协议 — SSL（安全套接字层）协议。

Fastly的Force TLS功能允许您强制将网站页面的所有传入未加密请求发送给TLS。

>>
它的工作方式是对任何未加密的请求返回&#x200B;*301 Moved Permanently*&#x200B;响应，该响应将重定向到等效的TLS。 例如，请求&#x200B;*http://www.example.com/foo.jpeg*&#x200B;将重定向到&#x200B;*https://www.example.com/foo.jpeg*。

[保护通信](https://docs.fastly.com/guides/securing-communications/)（Fastly文档）

## 受影响的版本

* 云基础架构上的&#x200B;**Adobe Commerce：**
   * 版本：2.1.4及更高版本
   * 计划：Adobe Commerce on cloud infrastructure入门计划架构和Adobe Commerce on cloud infrastructure Pro计划架构（包括Pro Legacy）
* **Fastly：** 1.2.4

## 路由不需要更改.yaml

若要在存储的&#x200B;**所有**&#x200B;页面上启用HTTP到HTTPS的重定向，则不必将这些页面添加到`routes.yaml`配置文件 — 仅需为整个存储启用“全局强制TLS”(使用Commerce管理员)即可。

## 相关Fastly文档

* 适用于Adobe Commerce 2的[强制TLS指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [强制TLS重定向](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [保护通信](https://docs.fastly.com/guides/securing-communications/)
