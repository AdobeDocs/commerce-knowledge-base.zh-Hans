---
title: 在[!UICONTROL CSP]限制模式下对storefront结账页面进行故障排除
description: 本文介绍了在CSP限制模式下查看签出页面时可能遇到的错误，并提供修复这些错误的解决方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 0%
---
# 在[!UICONTROL CSP]限制模式下对storefront结账页面进行故障排除

本文为在&#x200B;**[!UICONTROL CSP restricted mode]**&#x200B;中查看签出页面时Adobe Commerce 2.4.7问题提供了说明和修复，其中的“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令：“script-src ...*” 浏览器控制台日志中的错误消息。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、内部部署的Adobe Commerce和Magento Open Source：

* 2.4.7
* 2.4.6-pX
* 2.4.5-pX
* 2.4.4-pX

## 问题 — Storefront结帐页面已损坏或无法加载

**storefront checkout**&#x200B;页面已损坏或无法加载，因为“*Refused to execute inline script，因为它违反了以下内容安全策略指令：“script-src ...*” 浏览器控制台日志中的错误消息。

<u>重现步骤</u>：

1. 去店面。
1. 将产品添加到购物车并继续结帐。

<u>预期的结果</u>：

签出页面会正常完全加载。

<u>实际结果</u>：

签出页面为空或缺少组件。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认在`restrict-mode`中针对店面和管理区域中的付款页面进行配置，在所有其他页面中则以`report-only`模式进行配置。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因&#x200B;**[!UICONTROL CSP]**&#x200B;而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

**storefront checkout**&#x200B;页面上缺少付款方法或付款方法无法正常工作，带有“*Refused to execute inline script，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot; 浏览器控制台日志中的错误消息。

<u>重现步骤</u>：

1. 去店面。
2. 将产品添加到购物车并继续结帐。
3. 选择付款方式。

<u>预期的结果</u>：

您可以选择付款方式并继续成功下单。

<u>实际结果</u>：

付款方式缺失或无法正常工作。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认在`restrict-mode`中针对店面和管理区域中的付款页面进行配置，在所有其他页面中则以`report-only`模式进行配置。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因&#x200B;**[!UICONTROL CSP]**&#x200B;而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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

## 问题 — 客户无法下订单

客户无法下订单，因为“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令：&quot;script-src ...*&quot; 浏览器控制台日志中的错误消息。

<u>重现步骤</u>：

1. 去店面。
2. 将产品添加到购物车并继续结帐。
3. 选择付款方式。
4. 单击&#x200B;**下单**。

<u>预期的结果</u>：

您可以成功下订单。

<u>实际结果</u>：

你无法下订单。 浏览器控制台日志中显示以下[!DNL JS]错误： “*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中，**[!UICONTROL CSP]**&#x200B;默认在`restrict-mode`中针对店面和管理区域中的付款页面进行配置，在所有其他页面中则以`report-only`模式进行配置。
在付款页的`script-src`指令中，相应的&#x200B;**[!UICONTROL CSP]**&#x200B;标题不包含`unsafe-inline`关键字。 此外，只允许使用[!DNL whitelisted]内联脚本。

### 解决方案

由于某些脚本因&#x200B;**[!UICONTROL CSP]**&#x200B;而被阻止，用户可能会看到浏览器错误：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

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
