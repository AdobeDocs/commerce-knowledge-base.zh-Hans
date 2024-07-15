---
title: 在[!UICONTROL CSP]限制模式下创建订单页疑难解答
description: 本文介绍了在启用CSP限制模式时在管理员端创建订单时发生的错误，并提供修复这些错误的解决方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 在[!UICONTROL CSP]限制模式下创建订单页疑难解答

本文针对Adobe Commerce 2.4.7问题提供了说明和修复，当在管理员端使用&#x200B;**[!UICONTROL CSP restricted mode]**&#x200B;创建订单时，该问题为&#x200B;*已启用*，带有“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令：“script-src ...*”错误消息（在浏览器控制台日志中）。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、Adobe Commerce内部部署和Magento Open Source：

* 2.4.7
* 2.4.6像素
* 2.4.5-pX
* 2.4.4像素

## 问题 — 管理员&#x200B;**创建订单**&#x200B;页面已损坏或无法加载

管理员&#x200B;**创建订单**&#x200B;页面已损坏或无法加载，其中“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令：浏览器控制台日志中的“script-src ...*”错误消息。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 创建新订单。

<u>预期的结果</u>：

管理员&#x200B;**创建订单**&#x200B;页面将正常完全加载。

<u>实际结果</u>：

管理员&#x200B;**创建订单**&#x200B;页面为空或缺少组件。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认配置为`restrict-mode`，适用于店面和管理区域中的付款页面，以及所有其他页面的`report-only`模式。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因[!UICONTROL CSP]而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`类阻止的脚本。
1. 使用`CSPNonceProvider`类允许执行脚本。
Adobe Commerce和Magento Open Source 2.4.7及更高版本包含一个**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供程序，以便为每个请求生成唯一的[!DNL nonce]字符串。 然后将这些[!DNL nonce]字符串附加到[!UICONTROL CSP]标头。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函数获取[!DNL nonce]字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [将 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)添加到模块的`csp_whitelist.xml`文件。

## 问题 — 付款方法缺失或无法正常工作

管理员&#x200B;**订单创建页面**&#x200B;上缺少付款方法或付款方法不起作用，带有“*Refused to execute inline script，因为它违反了以下内容安全策略指令：浏览器控制台日志中的“script-src ...*”错误消息。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 创建新订单。
1. 创建新客户。
1. 输入客户详细信息。
1. 输入订单详细信息（产品、发运方法）。
1. 选择付款方式。

<u>预期的结果</u>：

您可以选择付款方式并继续成功下单。

<u>实际结果</u>：

付款方式缺失或无法正常工作。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;。

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认配置为`restrict-mode`，适用于店面和管理区域中的付款页面，以及所有其他页面的`report-only`模式。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因&#x200B;**[!UICONTROL CSP]**&#x200B;而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`类阻止的脚本。
1. 使用`CSPNonceProvider`类允许执行脚本。
Adobe Commerce和Magento Open Source 2.4.7及更高版本包含一个**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供程序，以便为每个请求生成唯一的[!DNL nonce]字符串。 然后将这些[!DNL nonce]字符串附加到[!UICONTROL CSP]标头。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函数获取[!DNL nonce]字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [将 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)添加到模块的`csp_whitelist.xml`文件。

## 问题 — 管理员无法下订单

管理员无法在管理员&#x200B;**创建订单页面**&#x200B;上提交订单，因为“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令：浏览器控制台日志中的“script-src ...*”错误消息。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 创建新订单。
1. 创建新客户。
1. 输入客户详细信息。
1. 输入订单详细信息（产品、发运方法）。
1. 选择付款方式。
1. 提交订单。

<u>预期的结果</u>：

您可以成功提交订单。

<u>实际结果</u>：

您无法提交订单。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认配置为`restrict-mode`，适用于店面和管理区域中的付款页面，以及所有其他页面的`report-only`模式。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因&#x200B;**[!UICONTROL CSP]**&#x200B;而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`类阻止的脚本。
1. 使用`CSPNonceProvider`类允许执行脚本。
Adobe Commerce和Magento Open Source 2.4.7及更高版本包含一个**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供程序，以便为每个请求生成唯一的[!DNL nonce]字符串。 然后将这些[!DNL nonce]字符串附加到[!UICONTROL CSP]标头。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函数获取[!DNL nonce]字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [将 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)添加到模块的`csp_whitelist.xml`文件。
