---
title: Adobe Commerce 2.3.6、2.4.1签出的验证码不起作用
description: 本文提供了一个修补程序，用于解决在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付提供商时，用于结账的CAPTCHA功能在“下单”页面上无法按预期工作的问题。
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6、2.4.1签出的验证码不起作用

本文提供了一个修补程序，用于解决在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付提供商时，用于结账的CAPTCHA功能在“下单”页面上无法按预期工作的问题。

我们的开发人员文档提到了此已知问题：

对于Adobe Commerce 2.3.6</u>：<u>

* [Adobe Commerce 2.3.6发行说明：已知问题](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/commerce-2-3-6.html)
* [Magento Open Source2.3.6发行说明：已知问题](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

对于Adobe Commerce 2.4.1</u>：<u>

* [Adobe Commerce 2.4.1发行说明：已知问题](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-1#known-issues)
* [Magento Open Source2.4.1发行说明：已知问题](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-1#known-issues)

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.6和2.4.1
* Magento Open Source2.3.6和2.4.1

## 问题

<u>重现步骤</u>

1. 在Commerce中至少设置以下一种支付方式：Paypal Express、Payflow Pro或CyberSource。
1. 转到&#x200B;**管理员>商店>配置>客户>客户配置>验证码** 。
   * 设置&#x200B;**在店面启用CAPTCHA** = *是* 。
   * 在&#x200B;**Forms**&#x200B;中选择： *签出/下单*、*登录*&#x200B;和&#x200B;*忘记密码* 。
   * 设置&#x200B;**显示模式** = *尝试登录的次数之后*（显示&#x200B;**尝试登录失败的次数**&#x200B;设置）。
   * 设置&#x200B;**失败的登录尝试次数** = *0*（使验证码始终有效）。
1. 在前端，将产品添加到购物车并尝试结帐。
1. 在支付信息页面上，输入captcha并尝试使用Paypal Express、Payflow Pro或CyberSource进行结账。

<u>预期结果：</u>

验证码功能按预期运行。

<u>实际结果：</u>

显示错误消息：*请提供CAPTCHA代码并重试。*

## 解决方案

根据您在Adobe Commerce本地/Adobe Commerce上部署的是cloud infrastructure/Magento Open Source 2.3.6还是2.4.1，应用以下修补程序之一。

## 补丁程序

修补程序已附加到此文章，可以两种格式`.composer`和`.git`下载。

要下载补丁程序，请向下滚动到文章的结尾并单击文件名，或单击以下链接之一：

<u>对于云基础架构上的Adobe Commerce内部部署/Adobe Commerce/Magento Open Source2.3.6</u>：

* [Composer修补程序MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修补程序MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>对于云基础架构上的Adobe Commerce内部部署/Adobe Commerce/Magento Open Source2.4.1</u>：

* [Composer修补程序MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修补程序MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

这些修补程序与任何其他Adobe Commerce或Magento Open Source版本不兼容。

## 如何应用修补程序

<u>Composer修补程序</u>

有关编辑器修补程序的说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

<u>Git修补程序</u>

有关Adobe Commerce/Magento Open Source的Git修补程序说明，请参阅开发人员文档[应用修补程序：自定义修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches)。
