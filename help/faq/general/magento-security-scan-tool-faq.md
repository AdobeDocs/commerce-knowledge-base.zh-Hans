---
title: Adobe Commerce安全扫描工具常见问题解答
description: 本文解答了一些有关Adobe Commerce安全扫描工具的常见问题(FAQ)。
exl-id: 380ce617-e3d9-491b-b425-8489abd3c541
feature: Compliance
source-git-commit: cff17a83648e10e85d95a5895acd8d1916a8eef9
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Adobe Commerce安全扫描工具常见问题解答

本文解答了一些有关Adobe Commerce安全扫描工具的常见问题(FAQ)。

## 安全扫描工具是什么，它是为谁编写的？ {#what-is-the-magento-security-scan-tool-and-who-is-it-written-for}

安全扫描工具是一种免费工具，可供我们的商家、开发人员和他们指定负责的人员，用于监控他们的站点是否存在安全风险。 它可以主动高效地检测商家商店中的恶意软件，并在存在任何安全风险、恶意软件或威胁时通知商家。

## 安全扫描工具是否适用于所有Adobe Commerce商家？ {#is-magento-security-scan-tool-available-to-all-magento-merchants}

是，安全扫描工具适用于所有Adobe Commerce和Magento Open Source商家。

## 有人可以使用安全扫描工具扫描我的网站吗？ {#can-anyone-scan-my-site-with-the-magento-security-scan-tool}

不会，当商家通过令牌请求扫描时，会将其网站绑定到其Adobe Commerce帐户。 每个站点的此项都是唯一的。

## 该工具能否扫描我网络商店中的非Adobe Commerce页面？ {#can-the-tool-scan-non-magento-pages-on-my-webstore}

安全扫描工具旨在扫描Adobe Commerce域上的漏洞。 使用安全扫描工具扫描非Adobe Commerce页面是否存在漏洞可能会导致结果不可靠。 我们强烈建议我们的商家不要使用安全扫描工具来扫描其他非Adobe Commerce平台生成的页面。

## 是否可以从扫描工具中排除特定的安全测试？ {#can-i-exclude-specific-security-tests-from-magento-scan-tool}

安全扫描工具商家无法从Adobe Commerce的安全扫描工具扫描中排除特定的安全测试。 每个安全扫描工具安全测试都旨在帮助商家识别安全风险、恶意软件和威胁。

## 价格是多少？ {#what-does-it-cost}

安全扫描工具是免费的。 商家必须接受一项法律免责声明，该声明根据安全扫描的结果或其站点的配置免除了Adobe Commerce的责任。

## 安全扫描工具如何工作？ {#how-does-the-magento-security-scan-tool-work}

安全扫描工具基于Web，可从商家的Adobe Commerce在线帐户([account.magento.com](https://account.magento.com/))访问。 安全扫描可通过HTTP和HTTPS运行。 它会检查已知的安全问题，并识别缺失的Adobe Commerce修补程序和更新。

## 如何注册使用安全扫描工具？ {#how-do-i-sign-up-to-use-the-magento-security-scan-tool}

商家可以注册使用安全扫描工具从其Adobe Commerce帐户([account.magento.com](https://account.magento.com))扫描其网上商店。 单击此链接注册安全扫描工具[此处](https://account.magento.com/scanner/dashboard/?_ga=2.83981338.267715797.1615821601-2099431409.1611073686)。

## 如果在扫描报告中遇到误报，我该怎么办？ {#what-do-i-do-if-i-come-across-a-false-positive-in-the-scan-report}

我们建议我们的商家调查所有失败的扫描，并采取适当步骤来解决此类问题。 调查后，如果商家遇到似乎误报的扫描结果，我们要求商家通知Adobe采取适当措施。

要提交误报报告，请输入具有Adobe Commerce商家支持的票证，以便我们能够评估误报、进行必要更改和/或提供建议以避免将来看到此类通知。
