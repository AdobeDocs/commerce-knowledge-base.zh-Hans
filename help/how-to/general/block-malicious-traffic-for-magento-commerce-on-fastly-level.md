---
title: 阻止Adobe Commerce在Fastly级别的恶意流量
description: 本文提供了当您怀疑云基础架构存储上的Adobe Commerce遇到DDoS攻击时，阻止恶意流量可以采取的步骤。
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 阻止Adobe Commerce在Fastly级别的恶意流量

本文提供了当您怀疑云基础架构存储上的Adobe Commerce遇到DDoS攻击时，阻止恶意流量可以采取的步骤。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.3.x

在本文中，我们假定您已经拥有恶意IP和/或其国家/地区和用户代理。 云基础架构上的Adobe Commerce用户通常从Adobe Commerce支持部门获取此信息。 以下部分提供了基于此信息阻止流量的步骤。 所有更改都应在生产环境中完成。

## 获取对管理面板的访问权限

如果您的网站因DDoS而过载，则可能无法登录到Commerce管理员（并执行本文中进一步描述的所有步骤）。

若要访问管理员，请按照[启用或禁用维护模式](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)并将IP地址列入白名单中的说明将网站置于维护模式。 完成后禁用维护模式。

## 按IP阻止流量

对于云基础架构存储上的Adobe Commerce而言，按特定IP地址和子网阻止流量的最有效方法是在Commerce管理员中为Fastly添加ACL。 以下步骤包含指向更详细说明的链接：

1. 在Commerce管理员中，导航到&#x200B;**商店** > **配置** > **高级** > **系统** > **全页缓存** > **快速配置**。
1. [创建一个新ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md)，其中包含您要阻止的IP地址或子网列表。
1. 将其添加到ACL列表并阻止，如Adobe Commerce的Fastly\_Cdn模块的[Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)指南中所述。

## 按国家/地区阻止流量

对于云基础架构存储上的Adobe Commerce，按国家/地区阻止流量的最有效方法是在Commerce管理员中为Fastly添加ACL。

1. 在Commerce管理员中，导航到&#x200B;**商店** > **配置** > **高级** > **系统** > **全页缓存** > **快速配置**。
1. 选择国家/地区并使用ACL配置阻止，如Adobe Commerce的Fastly\_Cdn模块的[Blocking](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)指南中所述。

## 按用户代理阻止流量

要基于用户代理建立阻止，您需要向Fastly配置添加自定义VCL代码片段。 为此，请执行以下步骤：

1. 在Commerce管理员中，导航到&#x200B;**商店** > **配置** > **高级** > **系统** > **全页缓存**。
1. 然后&#x200B;**Fastly配置** > **自定义VCL代码片段**。
1. 按照Fastly\_Cdn模块的[自定义VCL代码片段](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md)指南中的说明创建新的自定义代码片段。 您可以使用以下代码示例作为示例。 此示例不允许`AhrefsBot`和`SemrushBot`用户代理的流量。

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## 速率限制（实验性Fastly功能）

在云基础架构上，Adobe Commerce试验性的Fastly功能允许您为特定路径和爬网程序指定速率限制。 有关详细信息，请参阅[Fastly模块文档](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md)。

该功能必须先在暂存环境中进行全面测试，然后才能用于生产，因为它可能会阻止合法流量。

## 建议：考虑更新robots.txt

更新`robots.txt`文件有助于防止某些搜索引擎、爬网程序和机器人爬取某些页面。 例如，不应爬网的页面有搜索结果页面、结账、客户信息等。 阻止机器人爬行这些页面有助于减少这些机器人生成的请求数。

使用`robots.txt`时有两个重要注意事项：

* 机器人可以忽略您的`robots.txt`。 尤其是恶意软件机器人，它会扫描网页以发现安全漏洞，垃圾邮件发送者使用的电子邮件地址收集器不会引起注意。
* `robots.txt`文件是公开可用的文件。 任何人都可以看到您不希望机器人使用的服务器区域。

可在开发人员文档的[搜索引擎机器人](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots)文章中找到基本信息和默认Adobe Commerce `robots.txt`配置。

有关`robots.txt`的一般信息和建议，请参阅：

* [由Google支持创建robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt)文件
* [关于/robots.txt](https://www.robotstxt.org/robotstxt.html)，由robotstxt.org提供

与您的开发人员和/或SEO专家合作，确定要允许的用户代理或要禁止的用户代理。

## 相关阅读

* 云中Adobe Commerce的[产品特定许可条款](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* 在Commerce on Cloud指南中[用于阻止请求的自定义VCL](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
