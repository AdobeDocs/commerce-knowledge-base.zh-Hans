---
title: Adobe Commerce安全扫描工具疑难解答指南
description: 了解如何对Adobe Commerce和Magento Open Source的安全扫描工具的各种问题进行故障排除。
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---

# Adobe Commerce安全扫描工具疑难解答指南

了解如何对Adobe Commerce和Magento Open Source的安全扫描工具的各种问题进行故障排除。

## 问题：无法提交站点

安全扫描工具要求您先证明对网站的所有权，然后才能将域添加到安全扫描工具。 可以通过使用HTML注释或`<meta>`标记向您的网站添加确认代码来执行此操作。 HTML注释应放在`<body>`标记内，例如，页脚部分中。 `<meta>`标记应放置在页面的`<head>`部分中。

当安全扫描工具无法确认商户的网站所有权时，商户会遇到一个常见问题。

如果您收到错误并且无法提交站点以进行扫描，请参阅我们的支持知识库中的将站点添加到安全扫描中的[错误消息](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md)故障排除文章。

## 问题：安全扫描工具生成的空报告

您从安全扫描工具获取了空的扫描报告，或者获得的报告只包含一个错误，如&#x200B;*安全工具无法访问基本URL*，或者在提供的URL *上找不到* Magento安装。

### 解决方案

1. 检查52.87.98.44、34.196.167.176和3.218.25.102 IP是否未在80和443端口处被阻止。
1. 检查提交的重定向URL（例如，`https://mystore.com`重定向到`https://www.mystore.com`或反之，或者重定向到其他域名）。
1. 调查WAF/Web服务器访问日志中有关被拒绝/未完成的请求。 HTTP 403 `Forbidden`和HTTP 500 `Internal server error`是导致生成空报表的常见服务器响应。 以下是阻止用户代理请求的确认代码示例：

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

您还可以在我们的支持知识库中看到[安全扫描工具报告为空白](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md)文章，以了解更多信息。

## 问题：安全问题已解决，但在扫描中仍显示为易受攻击

您已解决安全问题，并期待安全扫描显示您不再容易受到新解决问题的攻击。 您反而会发现安全扫描生成的报告仍然报告您容易遭受安全问题的攻击。

### 原因

仅为`active`和`live`云项目收集云实例元数据，不是实时进程。

统计信息收集脚本每天运行一次，然后安全扫描工具必须稍后提取新数据。

预计的同步周期延迟最长为一周，最少需要24小时。

检查中可能会显示以下状态：

1. **通过**：安全扫描工具已扫描您更新的数据并批准更改。
1. **未知**：安全扫描工具还没有域的相关数据；请等待下一个同步周期。
1. **失败**：如果状态显示失败，您需要修复问题（启用2FA、更改管理员URL等）并等待下一个同步周期。

如果对实例进行更改后已过去24小时，并且这些更改未反映在安全扫描报告中，您可以[提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)。 在提交票证时提供存储URL。

## BotNet可疑故障

您会收到有关“BotNet可疑”故障的通知。

### 原因

1. 商店域名在2019年进入“潜在BotNet参与者列表”，它公开显示了管理面板、下载程序或RSS功能，并且/或者其URL在CC过滤论坛中被提及。
1. 警报可能是由存储损坏和/或恶意软件的迹象引起的，如页面上发现的JavaScript。
1. 它不一定是一个持续存在的问题。 如果该商店此前曾遭到破坏，其主机名仍会作为“受害者”名称在深色网上浮动。
1. 也有可能不是由Adobe Commerce造成，而是由于系统受损（在操作系统级别）所致。

### 解决方案

1. 检查新创建的SSH帐户、文件系统更改等。
1. 执行安全审查。
1. 查看Adobe Commerce版本并进行升级，尤其是当它仍在运行不再受支持的Magento 1时。
1. 如果问题仍然存在，请[提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)并提供商店URL。

## 问题：危害注入失败

您收到有关“泄露注入”失败的错误。

### 解决方案

1. 查看安全扫描工具报告中指示的脚本。
1. 查看主页源正文以了解内联脚本注入。
1. 执行系统配置更改审查，尤其是在`HTML head`分区值中的自定义`Miscellaneous HTML`和`footer`。
1. 执行代码和数据库审查，以发现不熟悉的更改和注入的恶意软件的迹象。

如果以上都不能解决问题，请[提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)，并从报告中提供商店URL和错误消息。

## 常见问题解答

### 安全扫描是否会影响我网站上的性能？

不适用。 安全扫描可像单个用户一样，逐个发出所有请求。 因此，安全扫描不应影响网站性能。

### Adobe Commerce会将安全扫描报告保留多长时间？

您可以从终端生成前10个报表。 如果需要更早的报表，请联系Adobe Commerce支持部门。

### 提交支持票证时需要什么信息？

请提供与为[安全扫描](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26357)、MAGEID和Cloud Project_ID提交的域名完全相同的域名。 请注意，对于本地Adobe Commerce，不需要Cloud Project_ID。

### 如果我从扫描工具扫描中删除存储区会发生什么情况？

如果删除存储提交，则将删除所有相关数据，包括扫描报告。 此操作不可逆。 删除商店域后提交商店域会创建“新建”提交。
