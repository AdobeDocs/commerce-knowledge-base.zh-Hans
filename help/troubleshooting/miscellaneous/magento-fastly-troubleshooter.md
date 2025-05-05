---
title: Adobe Commerce Fastly疑难解答
description: 这个Adobe Commerce用户快速故障诊断程序将根据您对看到的症状的反应，引导您找到解决方案。 单击问题以查看下一个选项或答案。
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Adobe Commerce Fastly疑难解答

这个Adobe Commerce用户快速故障诊断程序将根据您对看到的症状的反应，引导您找到解决方案。 单击问题以查看下一个选项或答案。

## 步骤1 — 验证Fastly服务 {#step-1}

+++**客户报告了一个与Fastly有关的问题。 Fastly服务停止了吗？**

a.是 — 检查[Fastly服务状态](https://status.fastly.com/)，并[提交Adobe Commerce支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 继续执行[步骤2](#step-2)。

+++

## 步骤2 — 检查VCL配置文件 {#step-2}

+++**运行Backend Tester时是否有任何错误？**

通过[后端测试器 — Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/)运行项目URL。 它显示了VCL配置文件的版本（如果页面可缓存）、Fastly模块的版本以及其他有用的故障排除信息。 你有任何错误吗？

a.是 — 您收到消息&#x200B;_插件VCL版本已过时！ 请重新上传。_&#x200B;有关此错误的解决方案，请参阅[Fastly错误：插件VCL版本已过时！ 请重新上传](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md)。\
b.否 — [步骤3](#step-3)。

+++

## 步骤3 — 检查图像优化错误 {#step-3}

+++**映像优化错误？**

a.是 — [启用图像优化时出错](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md)。\
b.否 — 通过在CLI/终端中运行来检查DNS： `dig [your website.com] + short`。 继续执行[步骤4](#step-4)。

+++

## 步骤4 — 验证DNS {#step-4}

+++**运行`dig`时会发生什么？**

运行`dig`时，它返回了指向prod.magentocloud.map.fastly.net或以下IP地址之一的记录（请参阅我们的开发人员文档中的[使用生产设置更新DNS配置](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings)）：

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a.是 — 问题与DNS无关。 继续执行[步骤5](#step-5)。\
b.否 — 问题可能与DNS有关。 客户应[检查DNS配置](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings)或联系其DNS提供商以获取更多信息。

+++

## 步骤5 — 确认连接 {#step-5}

+++**在CLI/终端中运行`curl -svo /dev/null "https://website.com"`时，是否返回“连接不安全”或“不安全”消息？**

a.是 — 这可能是证书问题。 在浏览器中访问网站，选择锁图标并查找证书过期日期。 继续执行[步骤6](#step-6)。\
b.否 — 访问[http://fastly-debug.com](https://www.fastly-debug.com/)并在[Adobe Commerce支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)中共享此信息。

+++

## 步骤6 — 确认您拥有有效的TSL证书 {#step-6}

+++**证书是否已过期？**

a.是 — 您需要向证书颁发机构(CA)续订TLS证书。\
b.否 — 您可能完全没有证书。 如果您拥有Adobe Commerce，我们建议您购买TLS证书。 如果您在云基础架构上的Adobe Commerce上，则可以拥有经过域验证的Let&#39;s Encrypt SSL/TLS证书来提供来自Fastly的安全HTTPS流量。 请参阅我们的开发人员文档中的[配置SSL/TLS证书](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)。

+++

[返回步骤1](#step-1)
