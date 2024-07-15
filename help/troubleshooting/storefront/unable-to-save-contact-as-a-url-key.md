---
title: 无法将*contact*另存为URL键
description: 当您无法将*contact*另存为产品或CMS页面的URL键（例如“/contact”）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 无法将&#x200B;*联系人*&#x200B;另存为URL键

当您无法将&#x200B;*contact*&#x200B;另存为产品或CMS页面的URL密钥（例如，“/contact”）时，本文提供了此问题的解决方法。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

无法使用术语&#x200B;*contact*&#x200B;作为URL键保存产品或CMS页面。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。

<u>重现步骤</u>：

创建一个CMS页面，并将&#x200B;*contact*&#x200B;作为URL键。

<u>预期的结果</u>：

该页面将与&#x200B;*联系人*&#x200B;一起保存为URL密钥。

<u>实际结果</u>：

无法保存该页面。 您收到错误：*在URL键字段中指定的值将生成一个已存在的URL。*

## 原因

*联系人*&#x200B;是在`vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`中定义的保留字。

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 解决方案

不能将术语&#x200B;*contact*&#x200B;用作URL密钥，但是，可以将术语&#x200B;*contact*&#x200B;与另一个字母或数字结合使用（例如，*contact1*&#x200B;和&#x200B;*contact2*）。 尽管术语不必是&#x200B;*contact+\&lt;其他数字或字母\>*，但只要长度不超过255个字符，术语可以是任何字符串。

执行以下步骤：

1. 登录到Commerce Admin。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**。
1. 单击&#x200B;**[!UICONTROL Add URL Rewrite]**。
1. 在[!UICONTROL Create URL Rewrite]下拉列表中选择&#x200B;*[!UICONTROL Custom]*。
   1. 在[!UICONTROL Request Path]中，键入“contact”。 请注意，[!UICONTROL Request Path]是用户在浏览器中输入的内容，[!UICONTROL Target Path]是它应重定向到的位置。
   1. 在[!UICONTROL Target Path]中，键入新的URL键（例如，“contact1”）。
   1. 在[!UICONTROL Redirect]下拉列表中选择&#x200B;*[!UICONTROL No]*。

## 相关阅读

* 用户指南中的[URL重写](https://docs.magento.com/user-guide/marketing/url-rewrite.html)。
* 我们用户指南中的[SEO最佳实践](https://docs.magento.com/user-guide/marketing/seo-best-practices.html)。
