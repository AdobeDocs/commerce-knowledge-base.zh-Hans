---
title: 无法将送货另存为URL键
description: 当您无法为产品或CMS页面将shipping保存为URL密钥（_例如， /shipping_）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 无法保存 _配送_ 作为URL键

当您无法将shipping另存为URL键时，本文提供了此问题的解决方法(_例如， /shipping_)对于产品或CMS页面。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

无法保存包含术语的CMS页面 _配送_ 在URL键中。

<u>重现问题的步骤</u>：

创建 **[!UICONTROL CMS page]** URL键为 _配送_.

<u>预期结果</u>：

页面保存方式 _配送_ 作为URL键。

<u>实际结果</u>：

发生此错误时，无法保存：
*在URL键字段中指定的值将生成已存在的URL。*

## 原因

送货是在中定义的保留字 `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 解决方案

不能使用术语 _配送_ （在您的URL密钥中） — 但是，您可以使用术语 _配送_ 与其他字母或数字组合(_例如， shipping1和shipping2_)。

虽然这个词不一定是 _配送_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>  — 只要长度不超过，该术语可以是任何字符串 *255* 个字符。

## 执行以下步骤：

1. 登录到Adobe Commerce管理员。
1. 转到 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 单击 **[!UICONTROL Add URL Rewrite]**.
1. 选择 **[!UICONTROL Custom]** 在 **[!UICONTROL Create URL Rewrite]** 下拉菜单。
   1. 键入 [!UICONTROL Request Path] 作为 **_配送_**.
   1. 在 **[!UICONTROL Target Path]**，键入新的URL键(_例如，“shipping1”_)。
   1. 选择 **[!UICONTROL No]** 在 **[!UICONTROL Redirect]** 下拉菜单。


      (**注意**：请求路径是用户在浏览器中输入的内容，Target路径是用户应重定向到的位置。)

此外，请避免使用这些标记为的关键字 *保留* 导致出现相同异常的关键字。 使用下面列出的这些关键字中的任意关键字作为URL键值将导致出现相同的错误。


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## 相关阅读

* [URL重写](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 在我们的促销用户指南中。
* [seo最佳实践](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我们的促销用户指南中……
