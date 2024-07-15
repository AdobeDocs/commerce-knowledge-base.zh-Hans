---
title: 店面未加载顶部导航面板
description: 本文为Varnish Edge Side Include (ESI)问题提供了配置解决方案，在该问题中，如果使用Varnish进行缓存，则店面不会显示某些页面的内容（通常是顶部导航面板）。
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 店面未加载顶部导航面板

本文为Varnish Edge Side Include (ESI)问题提供了配置解决方案，在该问题中，如果使用Varnish进行缓存，则店面不会显示某些页面的内容（通常是顶部导航面板）。

## 受影响的产品和版本

* Adobe Commerce 2.X.X
* 所有涂漆版本

## 问题

<u>先决条件</u>：

为您的Adobe Commerce商店安装和配置Varnish。

<u>重现步骤</u>：

1. 去店面。
1. 浏览商店页面。

<u>预期的结果</u>：

所有内容和所有页面块加载成功。

<u>实际结果</u>：

请注意，某些内容块（如顶部导航面板中的类别）未加载。 改为显示空白。

## 原因

出现该问题的可能原因如下：

* ESI包含标签是通过HTTPS访问协议生成的，而Varnish仅适用于HTTP。
* Varnish不处理JSON中的ESI。
* 响应标头对于Varnish太大；它无法处理它们。

## 解决方案

要解决此问题，您需要执行额外的Varnish配置并重新启动Varnish。

1. 作为具有`root`权限的用户，在文本编辑器中打开“消失”配置文件。 有关不同操作系统该文件可能位于何处的信息，请参阅我们的开发人员文档中的[修改Varnish系统配置](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl)。
1. 在`DAEMON_OPTS variable`中，添加`-p feature=+esi_ignore_https`、`-p  feature=+esi_ignore_other_elements`、`-p  feature=+esi_disable_xml_check`。 这类似于：

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. 保存更改并退出文本编辑器。
1. 在VCL配置文件中，通过增加以下参数的值来增加响应标头： `http_resp_hdr_len`、`http_resp_size`、`workspace_backend`。 请确保最后两个参数具有相似的值。
1. 更改此项时，需要运行`service varnish restart`以使更改生效。

## 相关阅读

* 在开发人员文档中[配置Varnish和您的Web服务器](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl)。
* [涂漆文档](https://varnish-cache.org/docs/5.1/reference/index.html)
