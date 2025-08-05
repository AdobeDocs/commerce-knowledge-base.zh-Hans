---
title: Fastly缓存在云基础架构上不起作用Adobe Commerce
description: 本文修复了Fastly缓存在您的网站上不起作用的问题。 Fastly是Adobe Commerce中包含的一项CDN和缓存服务，用于云基础架构计划和实施。 要验证Fastly扩展是否正常工作或者调试Fastly扩展，可以使用curl命令显示某些响应标头。 这些响应标头的值指示Fastly是否已启用以及是否正常运行。 您可以根据标头的值和缓存行为进一步调查问题。
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Fastly缓存在云基础架构上不起作用Adobe Commerce

本文修复了Fastly缓存在您的网站上不起作用的问题。 Fastly是Adobe Commerce中包含的一项CDN和缓存服务，用于云基础架构计划和实施。 要验证Fastly扩展是否正常工作或者调试Fastly扩展，可以使用curl命令显示某些响应标头。 这些响应标头的值指示Fastly是否已启用以及是否正常运行。 您可以根据标头的值和缓存行为进一步调查问题。

此信息可帮助您验证和测试实时网站和源服务器的Fastly标头。

## 受影响的版本

* 云基础架构上的Adobe Commerce
* Fastly 1.2.27及更高版本

## 问题

缓存可能不适用于实时站点、生产或暂存环境。

## 原因

通常，配置、不正确的凭据或不支持的Adobe Commerce扩展是Fastly缓存无法正常运行的问题。 如果您设置Fastly不正确，或者使用不受支持的扩展来删除标头，则Fastly缓存将无法正常工作。

## 使用命令进行测试并检查响应标头

### 使用dig命令进行测试

首先，使用指向URL的dig命令检查标头。 在终端应用程序中，输入dig `<url>`以验证Fastly服务是否显示在标头中。 有关其他挖掘测试，请参阅Fastly的[在更改DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains)之前进行的测试。

例如：

* 实时网站： `dig http[s]://<your domain>`
* 暂存： `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* 生产： `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### 使用curl命令进行测试

接下来，使用curl命令验证X-Magento-Tags是否存在以及其他标头信息。 对于“暂存”和“生产”，命令格式不同。

有关这些命令的更多信息，当您插入`-H "host:URL"`，替换为连接位置的源（OneDrive电子表格中的CNAME信息）时，会绕过Fastly，`-k`会忽略SSL，`-v`会提供详细响应。 如果标头显示正确，请检查实时网站并再次验证标头。

* 如果在绕过Fastly直接点击源服务器时出现标头问题，则您的代码、扩展或基础架构可能会出现问题。
* 如果您在直接命中源服务器时没有遇到错误，但标头通过Fastly命中活动域时缺失，则您可能会遇到Fastly错误。

首先，检查您的&#x200B;**活动站点**&#x200B;以验证响应标头。 命令通过Fastly扩展接收响应。 如果您没有收到正确的标头，则应该直接测试原始服务器。 此命令返回`Fastly-Magento-VCL-Uploaded`和`X-Cache`标头的值。

1. 在终端中，输入以下命令以测试您的实时网站URL：

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   仅当您的实时URL未使用DNS设置并且您没有静态路由集时才使用`--resolve`。 例如：

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. 验证响应标头以确保Fastly正常工作。 此命令的输出类似于curl Staging和Production。 例如，您应会看到此命令返回的唯一标头：

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

要测试&#x200B;**暂存**，请执行以下操作：

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

要测试&#x200B;**生产负载平衡器**，请执行以下操作：

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

要测试&#x200B;**生产源节点**，请执行以下操作：

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

直接源节点：

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

例如，如果您有一个公共URL www.mymagento.biz ，请输入类似于以下内容的命令来测试生产站点：

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### 检查响应标头

* 检查返回的响应标头和值：
* Fastly-Magento-VCL-Uploaded应存在
* 应返回X-Magento-Tags
* Fastly-Module-Enabled应为Yes或Fastly扩展版本号
* X-Cache应为“点击”或“点击”、“点击”
* x-cache-hits应为1,1
* Cache-Control： max-age应大于0
* Pragma应为缓存

以下示例显示了Pragma、X-Magento-Tags和Fastly-Module-Enabled的正确值。

curl命令的输出可能会很长。 以下是仅供参考的摘要：

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## 解决

### Fastly-Module-Enabled不存在

如果您未在响应标头中收到“是”的“Fastly-Module-Enabled”，则需要验证是否已安装和选择Fasty模块。

要验证是否已在暂存和生产环境中启用Fastly，请在Commerce管理员中检查每个环境的配置：

1. 使用带有/admin的URL（或已更改的管理员URL）登录Admin Console以进行暂存和生产。
1. 导航到存储>配置>高级>系统。 滚动并单击全页缓存。
1. 确保选择Fastly CDN。
1. 单击Fastly配置。 确保输入Fastly服务ID和Fastly API令牌（您的Fastly凭据）。 验证您是否已为暂存环境和生产环境输入正确的凭据。 单击“测试凭据”可提供帮助。
1. 编辑您的composer.json并确保版本中包含快速模块。 此文件的所有模块都列出了版本。

   * 在“需要”部分中，您应该具有“fastly/magento2”： `<version number>`
   * 在“存储库”部分中，您应具有：

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. 如果使用配置管理，则应该有一个配置文件。 编辑app/etc/config.app.php (2.0， 2.1)或app/etc/config.php (2.2)文件，并确保设置`'Fastly_Cdn' => 1`正确。 设置不应为`'Fastly_Cdn' => 0`（表示已禁用）。如果您启用了Fastly，请删除配置文件并运行bin/magento magento-cloud:scd-dump命令进行更新。 有关该文件的演练，请参阅配置指南中的[管理系统特定设置示例](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=zh-Hans#manage-the-system-specific-configuration)。

如果未安装该模块，则需要在[集成环境](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-27242)分支中安装并部署到暂存和生产环境。 有关Commerce on Cloud Infrastructure指南中的说明，请参阅[设置Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hans)。

### Fastly-Magento-VCL-Uploaded不存在

在安装和配置期间，您应该已上传Fastly VCL。 这些是Fastly模块提供的基本VCL片段，而不是您创建的自定义VCL片段。 有关说明，请参阅Commerce on Cloud Infrastructure指南中的[上传Fastly VCL代码片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hans#upload-vcl-to-fastly)。

### X-Cache包括MISS

如果X-Cache为HIT、MISS或MISS、MISS，请再次输入相同的curl命令以确保该页面最近没有从缓存中撤出。

如果您获得相同的结果，请使用curl命令并验证响应标头：

* Pragma是缓存
* X-Magento-Tags已存在
* Cache-Control： max-age大于0

如果问题仍然存在，则其他扩展可能会重置这些标头。 在暂存中重复以下过程可禁用扩展，以查找导致问题的扩展。 找到导致问题的扩展后，您将需要在生产环境中禁用该扩展。

1. 要禁用扩展，请按照Commerce on Cloud Infrastructure指南的[管理扩展](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=zh-Hans#manage-extensions)部分中给出的步骤操作。
1. 禁用扩展后，转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**。
1. 单击&#x200B;**[!UICONTROL Flush Magento Cache]**。
1. 现在，每次启用一个扩展，以保存配置并刷新缓存。
1. 尝试curl命令并验证响应标头。
1. 重复步骤4和5以启用和测试curl命令。 当Fastly标头不再显示时，您发现扩展导致Fastly出现问题。

当您隔离正在重置Fastly标头的扩展时，请与扩展开发人员联系以获取其他帮助。 我们无法向第三方扩展开发人员提供修复或更新以用于Fastly缓存。

## 有关更多信息，请参阅我们的开发人员文档：

* [关于Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=zh-Hans)
* [设置Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hans)
* [自定义Fastly VCL代码片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=zh-Hans)
