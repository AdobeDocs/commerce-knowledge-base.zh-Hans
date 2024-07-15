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

# 无法将&#x200B;_shipping_&#x200B;另存为URL键

当您无法为产品或CMS页面将shipping保存为URL密钥（_例如， /shipping_）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

无法在URL键中保存术语为&#x200B;_shipping_&#x200B;的CMS页面。

<u>重现步骤</u>：

创建URL键为&#x200B;_shipping_&#x200B;的&#x200B;**[!UICONTROL CMS page]**。

<u>预期的结果</u>：

该页面将以&#x200B;_shipping_&#x200B;作为URL键进行保存。

<u>实际结果</u>：

发生此错误时，无法保存：
*在URL键字段中指定的值将生成一个已存在的URL。*

## 原因

送货是在`vendor/magento/module-shipping/etc/frontend/routes.xml`中定义的保留字。

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 解决方案

无法在URL密钥中使用术语&#x200B;_shipping_，但可以将术语&#x200B;_shipping_&#x200B;与另一个字母或数字（_例如，shipping1和shipping2_）结合使用。

尽管术语不必是&#x200B;_发货_+&lt;其他数字或字母> — 术语可以是任何字符串，只要长度不超过&#x200B;*255*&#x200B;个字符。

## 执行以下步骤：

1. 登录到Adobe Commerce管理员。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**。
1. 单击&#x200B;**[!UICONTROL Add URL Rewrite]**。
1. 在&#x200B;**[!UICONTROL Create URL Rewrite]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Custom]**。
   1. 键入[!UICONTROL Request Path]为&#x200B;**_shipping_**。
   1. 在&#x200B;**[!UICONTROL Target Path]**&#x200B;中，键入新的URL密钥（_例如，“shipping1”_）。
   1. 在&#x200B;**[!UICONTROL Redirect]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL No]**。


      （**注意**：请求路径是用户在浏览器中输入的内容，目标路径是用户应重定向到的路径。）

此外，请避免使用这些标记为&#x200B;*保留*&#x200B;关键字的关键字，这会导致出现相同的异常。 使用下面列出的这些关键字中的任意关键字作为URL键值将导致出现相同的错误。


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

* 在我们的促销用户指南中，[URL重写了](https://docs.magento.com/user-guide/marketing/url-rewrite.html)。
* 我们的《推销和促销用户指南》中的[SEO最佳实践](https://docs.magento.com/user-guide/marketing/seo-best-practices.html)。
