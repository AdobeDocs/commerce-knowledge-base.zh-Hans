---
title: Adobe Commerce支持知识库
description: 排除Commerce商店故障和维护所需了解的一切。
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">安全扫描工具返回“无法确定服务器是否使用2FA”：</a>若要解决此错误，请检查<code>Magento_TwoFactorAuth</code>模块是否已禁用。 通常，要通过检查，应该启用它。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632：每次尝试订购时保存的地址：</a> ACSD-60632修补程序修复了在每次尝试订购时保存新地址的问题，无论是否成功创建了订单。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326：关于客户退货状态的GraphQL查询出现错误：</a> ACSD-60326修补程序修复了GraphQL查询客户退货状态时出现错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925：在GraphQL中按位置对媒体集中的项目进行排序：</a> ACSD-59925修补程序修复了媒体集中的项目未按位置排序，从而导致显示顺序不正确的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322：未分配给共享目录的产品包含在XML站点地图中： </a> ACSD-61322修补程序修复了未分配给默认（常规）组的共享目录的产品/类别仍包含在XML站点地图中的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590：增强了Bestsellers汇总每日报表生成的性能：</a> ACSD-60590修补程序修复了Bestsellers汇总每日报表需要大量时间才能为大量下订单生成的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865：由于产品数量不足，购物车价格规则无法取消以前的规则：</a> ACSD-59865修补程序修复了<em>固定金额折扣</em>、<em>产品价格折扣百分比</em>和<em>购买X获取Y</em>购物车价格规则不再取消以前规则的操作的问题。 <em></em>安装[!DNL Quality Patches Tool (QPT)] 1.1.52时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">在管理员中筛选订单时出错：</a>本文为Adobe Commerce问题提供了一个修补程序，该问题导致在尝试按日期在管理员中筛选订单时出现错误，显示消息： <em>完整性约束违规： 1052列“created_at”，其中where子句不明确</em>。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce：在内容安全策略(CSP)限制模式下，签出页面出现内联JavaScript问题：</a>本文为启用<strong>CSP限制模式</strong>时，在Adobe Commerce 2.4.7中通过Adobe Commerce Admin和Google Tag Manager添加的自定义JavaScript遇到的问题提供了详细的解释和解决方案。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195：购物车GraphQL请求无法返回最终页面上的项目：</a> ACSD-61195修补程序修复了在购物车GraphQL请求的最后一页上未返回购物车项目的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514：使用页面生成器的管理员中的Forms在浏览器控制台中引发错误：</a> ACSD-59514修补程序修复了使用页面生成器的管理员中的表单引发错误<em>页面生成器在提交表单后在浏览器控制台中呈现5秒且未释放锁定</em>的问题，并且无法保存更改。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538：如果在<em>所有商店视图</em>中禁用了产品，则属性无法正确显示</a> ACSD-60538修补程序修复了以下问题：如果在<em>所有商店视图</em>中禁用了产品，并且仅在特定商店视图范围内启用了产品，则产品属性无法在GraphQL响应中正确显示，从而导致产品无法正确显示。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352：通过GraphQL API返回默认存储的返回属性标签：</a>ACSD-58352修补程序修复了在请求标头中指定非默认存储视图时，通过GraphQL API返回默认存储的返回属性标签的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">您的帐户中缺少<em>Switch Accounts</em>下拉列表：</a>本文为Adobe Commerce问题提供了一个解决方案，该问题导致您的帐户中缺少<em>Switch Accounts</em>下拉列表，并且您失去了代表商家提交票证的访问权限。
    </td>
    <td>新文章</td>
    <td>2024年10月17</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979：删除暂存更新后删除的产品映像：</a>ACSD-56979修补程序修复了在删除暂存更新后删除产品映像的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.49时，此修补程序可用。  
    </td>
    <td>新文章</td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210：存储视图特定的作用域属性覆盖全局值：</a>ACSD-48210修补程序修复了在特定存储视图内更新<em>网站作用域</em>属性时覆盖全局作用域中的属性值的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280： 2.4.4-pX安装中的ReflectionUnionType：：getName()错误：</a> ACSD-59280修补程序修复了在安装2.4.4-pX版本期间调用未定义的方法<code>ReflectionUnionType::getName()</code>错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887：客户购物车在客户会话过期后被清除：</a>ACSD-54887修补程序修复了在客户会话过期后客户购物车被清除的问题，并启用了<em>永久购物车</em>。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303：启用HTML缩小后解决了管理员订单下达问题：</a> ACSD-60303修补程序修复了启用HTML缩小后无法下达管理员订单的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045： URL重写导致在<em>从层次结构中取消选中网站根</em>后出现无限页面循环：</a>ACSD-57045修补程序修复了URL重写导致在从层次结构中取消选中<em>网站根</em>后出现无限页面循环的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.49时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446：通过GraphQL删除具有子用户或团队的团队会给出一条不提供信息的错误消息：</a> ACSD-58446修补程序修复了Adobe Commerce问题，该问题导致通过GraphQL删除具有子用户或团队的团队会返回一条与UI不一致的未提供信息的错误消息。 安装[!DNL Quality Patches Tool (QPT)] 1.1.49时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735：在商店视图级别添加视频时，未正确配置YouTube API密钥会导致错误：</a> ACSD-58735修补程序修复了在商店视图级别添加YouTube视频时，错误YouTube API密钥配置会导致错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.49时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086：来自启用了条款和条件的非默认网站的订单处理不正确：</a> ACSD-57086修补程序修复了来自启用了条款和条件的非默认网站的订单处理不正确的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.49时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141：如果启用了L2 Redis缓存，则会在已登录客户的POST请求上重新生成PHPSESSID：</a> ACSD-58141修补程序修复了以下问题：如果启用了L2 Redis缓存，并且从Admin更新了客户，则会在已登录客户的POST请求上重新生成PHPSESSID。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790：修复了Chrome上移动设备视图中产品详细信息页面图像的缩放缩放功能：</a> ACSD-58790修补程序修复了Chrome上移动设备视图中的图像未按预期放大图像的Adobe Commerce问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。 
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442：修复了宽度为768px的设备被视为移动设备，导致菜单和标头在移动视图中加载而不是在桌面加载的问题：</a> ACSD-58442修补程序修复了Adobe Commerce的问题，该问题导致宽度为768px的设备被视为移动设备，导致菜单和标头在移动视图而不是桌面中加载。 安装[!DNL Quality Patches Tool (QPT)] 1.1.50时，此修补程序可用。
    </td>
    <td>新文章 </td>
    <td>2024年10月17</td>
  </tr>
</table>
