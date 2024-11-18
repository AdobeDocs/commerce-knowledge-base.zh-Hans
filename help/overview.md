---
title: Adobe Commerce支持知识库
description: 排除Commerce商店故障和维护所需了解的一切。
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Adobe Commerce支持知识库

>[!NOTE]
>
>Adobe Commerce支持知识库指南将很快进行重组，其内容将移至Adobe Experience League中的其他位置。 与此同时，我们将继续维护和更新本指南中的内容。

![知识库主页](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

此知识库中的信息旨在补充[Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs)、[Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)及其他Adobe Commerce出版物。 它涵盖故障排除和最佳实践，发布公告，回答常见问题，并重点说明官方文档中未提及（出于任何原因）的特定场景。

## 此知识库中包含哪些内容？

| 类别 | 描述 |
| --- | --- |
| [支持工具](/help/support-tools/overview.md) | 使用Adobe Commerce提供的各种支持工具改善您的电子商务商店体验。 我们提供个性化的最佳实践、诊断和监控工具，以及有关您站点的最相关信息。 |
| [公告](/help/announcements/overview.md) | 从 Adobe Commerce 团队获取重要更新。 |
| [疑难解答](/help/troubleshooting/overview.md) | 从Adobe Commerce支持团队获取自助解决方案和修补程序。 |
| [帮助中心用户指南](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | 了解如何有效地管理支持工单、授予共享访问权限和浏览知识库。 |
| [操作说明](/help/how-to/overview.md) | 从Adobe Commerce支持团队获取明确的分步说明。 |
| [常见问题解答](/help/faq/overview.md) | 查找有关Adobe Commerce策略、策略的常见问题解答以及有关Adobe Commerce功能的详细信息。 |

## 新增功能

<table style="width:100%">
  <tr>
    <th style="width:70%">描述</th>
    <th style="width:15%">类型</th>
    <th style="width:15%">日期</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">由于重组而转移许可证：</a>本文将帮助您轻松转移Adobe Commerce帐户所有权，包括保持服务无中断运行所需的所有必要步骤。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">可用于Adobe Commerce的安全更新(APSB24-90)：</a>在2024年11月12日，Adobe发布了Adobe Commerce（云和本地）的安全更新以及由Commerce服务提供支持并部署为SaaS（软件即服务）的Magento Open Source功能。 此更新解决了<a href="https://helpx.adobe.com/security/severity-ratings.html">严重</a>漏洞。 
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">MageID帐户所有者无法登录并提交支持票证：</a>本文解决了Adobe Commerce问题，即您无法登录account.magento.com上的帐户(MageID)提交支持票证。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">Adobe Commerce的OOTBBraintree扩展不支持最新的Visa 3DS字段：</a>本文介绍如何遵守新的Visa法规，因为Adobe Commerce的开箱即用Braintree扩展不支持最新的Visa 3DS字段。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528：使用GraphQL检索角色时未返回任何结果：</a> ACSD-61528修补程序修复了使用GraphQL从公司管理员处检索角色时始终返回null结果的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.53时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318： system.log：</a>中的环境模拟嵌套错误ACSD-48318修补程序修复了以下问题： <code>system.log</code>中每次发送发票电子邮件时都显示错误消息<em>main。错误：不允许环境模拟嵌套</em>。 安装[!DNL Quality Patches Tool (QPT)] 1.1.53时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366：删除团队列表中未显示已停用用户的团队：</a> ACSD-59366修补程序修复了当您尝试删除团队时出错的问题，该团队包含未在团队列表中显示的已停用用户。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234：应用折扣时PayPal显示的金额不正确：</a>ACSD-60234修补程序修复了通过付款方式应用折扣时[!DNL PayPal]显示不正确金额的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673：针对结账时的多种付款方式修复了购物车价格规则问题：</a> ACSD-60673修补程序修复了以下问题：使用付款方式条件的[!UICONTROL Cart Price Rule]的折扣并不总是列在总数中。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584：允许为一个网站创建的访问令牌访问其他网站上的信息：</a> ACSD-60584修补程序修复了允许为一个网站上的用户创建的访问令牌访问或更改其他网站上的客户信息的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.53时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788：由于内容安全策略错误，Google Tag Manager的自定义脚本未执行：</a> ACSD-60788修补程序修复了由于内容安全策略错误而无法执行[!DNL Google Tag Manager]的自定义脚本的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366： <code>bin/magento setup:static-content:deploy --jobs 4</code>命令遇到多个作业失败并出现错误：</a> ACSD-61366修补程序修复了<code>bin/magento setup:static-content:deploy --jobs 4</code>命令遇到多个作业失败并出现<em>端口的问题，必须在主机参数</em>错误中配置该命令，即使为数据库连接指定了端口也是如此。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816： APM代理插入的New Relic浏览器监视脚本与CSP不兼容：</a> ACSD-60816修补程序修复了APM代理插入的[!DNL New Relic]浏览器监视脚本与内容安全策略(CSP)不兼容的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952：删除与其他共享目录具有相同组ID的共享目录时出错：</a> ACSD-59952修补程序修复了在删除与其他共享目录具有相同的<code>customer_group_id</code>的共享目录时引发的错误。 它还可防止用户创建此类共享目录。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786：在获取过期报价的<code>quote_id</code>时，GraphQL返回错误：</a>ACSD-59786修补程序修复了GraphQL查询在获取过期报价的<code>quote_id</code>时返回错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967： JavaScript错误导致Google映射无法正确呈现：</a> ACSD-59967修补程序修复了JavaScript错误导致[!DNL Google Maps]无法正确呈现的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930：改进公司流程的性能：</a> ACSD-59930修补程序修复了在创建、保存或删除地址簿中地址超过1000个的管理员的公司时，管理员面板中显示<em>超时</em>错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.53时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年11月14日</td>
  </tr>
</table>
