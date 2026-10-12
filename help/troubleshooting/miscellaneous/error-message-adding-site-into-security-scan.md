---
title: 将站点添加到安全扫描时出现错误消息
description: 当用户无法将站点添加到[Commerce安全扫描](https://account.magento.com/scanner/dashboard/)时，本文提供该问题的可能解决方案。
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# 将站点添加到安全扫描时出现错误消息

当用户无法将站点添加到[Commerce安全扫描](https://account.magento.com/scanner/dashboard/)时，本文提供该问题的可能解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法和版本）
* Magento Open Source

## 问题

用户无法将站点添加到[Commerce安全扫描](https://account.magento.com/scanner/dashboard/)。 尝试添加站点时出现以下错误消息： *无法提交站点进行扫描。*

## 解决方案

1. 确保端口80和443上未阻塞以下IP地址：
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. 确认代码是区分时间的。 如果单击&#x200B;**添加站点**&#x200B;链接后已超过30分钟，则代码可能已过期。
1. 不要忘记清理缓存，并确保验证代码显示在主页源正文中。 确认代码应根据HTML标记规范插入：HTML注释可插入页体（我们建议将其放在页脚部分）；META标记应仅位于头部分。
1. 在单击&#x200B;**验证确认代码**&#x200B;之前，请打开浏览器的开发人员控制台，单击&#x200B;**网络**&#x200B;选项卡，然后检查来自magento.com的响应。 它应该为HTTP 200 (OK)，并且响应正文应包含一个JSON对象。
1. 如果响应代码是HTTP 200，并且响应正文是JSON对象，且`verified`属性值是`false`，则表示在页面上未找到该代码。 `details`属性值应包含说明。 例如，如果存储使用自签名SSL证书，则可能会出现连接错误。

如果仍无法添加站点，请完成以下步骤：

1. 在页面上再添加一个HTML评论：

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. 提交支持票证并提供以下信息：
   * Adobe Commerce store URL
   * MAGEID + Magento.com帐户电子邮件
   * 名字+姓氏
   * 公司名称
   * 逗号分隔通知电子邮件列表

## 相关阅读

* 用户指南中的[安全扫描](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)。
