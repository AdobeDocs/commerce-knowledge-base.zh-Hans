---
title: Adobe Commerce支持知识库
description: 排除Commerce商店故障和维护所需了解的一切。
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 738a5455267647d294d222d5bb6149254dcb93dd
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Adobe Commerce支持知识库

![知识库主页](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

此知识库中的信息旨在补充[Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs)、[Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)及其他Adobe Commerce出版物。 它涵盖故障排除和最佳实践，发布公告，回答常见问题，并重点说明官方文档中未提及（出于任何原因）的特定场景。

## 知识库中的内容

| 类别 | 描述 |
| --- | --- |
| [支持工具](/help/support-tools/overview.md) | 使用Adobe Commerce提供的各种支持工具改善您的电子商务商店体验。 我们提供个性化的最佳实践、诊断和监控工具，以及有关您站点的最相关信息。 |
| [公告](/help/announcements/overview.md) | 从 Adobe Commerce 团队获取重要更新。 |
| [疑难解答](/help/troubleshooting/overview.md) | 从Adobe Commerce支持团队获取自助解决方案和修补程序。 |
| [帮助中心用户指南](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | 了解如何有效地管理支持工单、授予共享访问权限和浏览知识库。 |
| [操作说明](/help/how-to/overview.md) | 从Adobe Commerce支持团队获取明确的分步说明。 |
| [常见问题解答](/help/faq/overview.md) | 查找有关Adobe Commerce策略、策略的常见问题解答以及有关Adobe Commerce功能的详细信息。 |

>[!NOTE]
>
>要提交新票证，请登录到[Adobe Commerce帮助中心](https://support.magento.com/)，然后按照[提交支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)中详述的步骤操作。
>
>如果您看不到提交票证的选项，请参阅[帮助中心用户指南](/help/help-center-guide/help-center/magento-help-center-user-guide.md)中的&#x200B;*[提交未显示的票证链接](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)*&#x200B;部分。

## 新增功能

<table style="width:100%">
  <tr>
    <th style="width:70%">描述</th>
    <th style="width:15%">类型</th>
    <th style="width:15%">日期</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment"> <code>Magento-cloud</code> CLI未显示活动环境：</a>有多个活动环境，您正在尝试通过运行Magento-cloud CLI （命令行工具）命令与环境交互。 但是，提示选择所需环境时不会列出此环境。
    </td>
    <td>新文章</td>
    <td>2024年7月30日</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">如何获取和应用安全修补程序：</a>本文提供了有关如何获取和应用已发布的安全修补程序的说明，但说明不可用。  
    </td>
    <td>新文章</td>
    <td>2024年7月30日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">当搜索引擎设置为Opensearch时，回退到Elasticsearch7：</a>本文为以下问题提供了解决方案：当搜索引擎在Adobe Commerce中设置为OpenSearch时，出现回退到Elasticsearch7错误。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">部署失败：“cache”命名空间错误中未定义命令：</a>本文为部署失败并且日志中显示的一个错误为<em>在“cache”命名空间中未定义命令</em>时的问题提供了解决方案。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566： <code>mergeCart</code>突变失败，GraphQL响应中出现内部服务器错误：</a> ACSD-55566修补程序修复了<code>mergeCart</code>突变失败的问题，GraphQL响应中出现内部服务器错误。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。  
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546：可配置和捆绑产品在店面显示为缺货：</a> ACSD-56546修补程序修复了可配置和捆绑产品在店面显示为缺货的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。  
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565：订单仪表板显示不正确的订单信息：</a> ACSD-57565修补程序修复了在更新时间段之前，订单仪表板显示不正确的订单信息的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394： GraphQL中按多个排序属性对产品排序不正确：</a>ACSD-57394修补程序修复了在GraphQL中使用多个排序属性时产品排序不正确的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854： GraphQL响应包含不应该在类别聚合中列出的禁用类别：</a> ACSD-57854修补程序修复了GraphQL响应包含不应该在类别聚合中列出的禁用类别的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074： <code>attribute_code</code>属性中带有<code>price_*</code>前缀的“是”/“否”自定义属性不适用于索引：</a> ACSD-57074修补程序修复了<code>attribute_code</code>属性中带有<code>price_*</code>前缀的<em>是”/“否”</em>自定义属性不适用于索引的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241：“已使用”和“已使用时间”属性为生成的优惠券显示不正确的值：</a> ACSD-55241修补程序修复了“已使用”和“已使用时间”属性为生成的优惠券显示不正确值的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760：管理员用户仅限访问特定网站，无法排序或添加新产品：</a> ACSD-56760修补程序修复了以下问题：管理员用户仅限访问特定网站，如果网络商店拥有自己的根类别，则无法在类别中排序或添加新产品。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635：帐户共享设置为全局时，导入的客户使用相同的电子邮件地址重复：</a> ACSD-56635修补程序修复了在帐户共享设置为全局的情况下使用导入时，导入的客户使用相同的电子邮件地址重复的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315：每次单击提取按钮时，在PayPal Payflow Pro中都会创建新交易记录：</a>ACSD-57315修补程序修复了每次在“管理员”的“查看交易记录”屏幕上单击提取按钮时，在PayPal Payflow Pro中创建新交易记录的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741：自定义MySQL触发器数据库设置错误疑难解答：</a> ACSD-56741修补程序修复了以下问题：由于数据库中与索引和MView无关的自定义MySQL触发器，在<code>setup:upgrade</code>期间出现错误消息<em>尝试访问null类型的值</em>上的数组偏移。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008：将结束日期编辑为空会导致计划更新消失：</a> ACSD-58008修补程序修复了将结束日期编辑为空会导致计划更新消失的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337：具有访问限制的管理员用户可以查看公司网格中的所有公司：</a> ACSD-57337修补程序修复了具有特定网站访问限制的管理员用户可以查看公司网格中所有网站的公司的问题。 安装<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">在<code>env:COMPOSER_AUTH</code>或<code>auth.json</code>中部署失败且访问密钥正确：</a>本文为部署失败并出现错误（如部署日志中的错误）时的问题提供了解决方案。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">如何针对GraphQL请求绕过WAF：</a>本文介绍当Fastly WAF阻止您的GraphQL请求时，如何针对GraphQL请求绕过WAF。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">电子邮件声明导出存储已几乎满：</a>本文为您收到一封声明导出存储已几乎满的电子邮件这一问题提供了解决方案。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">将MariaDB 10.4升级到10.5 for Adobe Commerce on cloud：</a>本文介绍如何从MariaDB 10.4升级到10.5，以继续使用云基础架构上的Adobe Commerce。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">所有Adobe Commerce版本上的修订版Google映射修补程序访问丢失：</a>本文为与3.54+以上的任何最新Google映射版本不兼容的Adobe Commerce商家提供了修补程序。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">可用于Adobe Commerce的安全更新 — APSB24-40：</a>本文共享与CVE-2024-34102相关的更新。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">集成环境中性能不佳的问题：</a>本文针对Pro集成环境和入门暂存环境性能不佳的问题提供了解决方案。 
    </td>
    <td>新文章 </td>
    <td>2024年7月30日</td>
 </tr>
</table>

## 受欢迎的文章

* [在Cloud 2.4.4上切换到OpenSearch for Adobe Commerce](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Adobe Commerce中的Apache log4j2漏洞](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [可用于Adobe Commerce APSB22-12的安全更新](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [识别和测量云基础架构上Adobe Commerce的中断](/help/how-to/general/how-to-identify-outages.md)
* [在Adobe Commerce上的群集中查看环境vCPU层](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [云基础架构上的Adobe Commerce：CPU分配计算](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [云基础架构上的Adobe Commerce：检查主机的CPU配置](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
