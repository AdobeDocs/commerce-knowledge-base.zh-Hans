---
title: Adobe Commerce版本的更新生命周期策略常见问题解答
description: Adobe Commerce为次要版本提供了质量修复，修复时间为从下一个次要软件版本正式发布之日起至少12个月。 我们在此期间提供质量修复的方式正在发生变化：
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 2898089896cc2cdc88110a999564669341a52136
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---

# Adobe Commerce版本的更新生命周期策略常见问题解答

## 有什么变化？

Adobe Commerce为次要版本提供了质量修复，修复时间为从下一个次要软件版本正式发布之日起至少12个月。 我们在此期间提供质量修复的方式正在发生变化：

* **以前的策略：**&#x200B;目前，对12个月EOS窗口内的上一行的质量修复是通过我们的季度修补程序版本提供的，因此季度修补程序是安全和质量的组合。
* **新策略：**&#x200B;从2.4开始，作为最新的次发行版本行，以前支持的行(2.3)的发行修补程序将变为仅安全版本。 在发布次要（如2.4）和后续的新次要发布行之后，我们仍将在12个月的时间内提供上一受支持行的质量修复；但这些修复将通过[质量修补程序工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)提供，并且仅侧重于严重问题。

## 此策略何时生效？

Adobe Commerce 2.3.6计划于2020年10月15日发布，并计划作为Adobe Commerce 2.3的最新补丁发行版本，其中将同时包含质量和安全性。 在2.3.6之后，2.3.x线路将变成仅限安全线路，并且可通过QPT修复2.3的关键质量问题。

>[!NOTE]
>
>我们唯一要发布2.3完整版本就是我们需要保持与技术栈栈(如PHP或Elasticsearch)的合规性。 此更新将于2021年第2季度进行，届时必须对PHP 7.4进行更新，我们会将行增加到2.3.7。有关详细信息，请参阅对Adobe Commerce 2.3.x版本行](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946)的DevBlog帖子[PHP 7.4支持。

## 什么是仅安全发行版？

仅限安全的发行版本仅包含安全修复，未修复任何质量。 但是，请注意，当我们认为特定修补程序对于运行Adobe Commerce绝对关键时，我们仅用于安全的版本可能包含这些修补程序。

## 最新一行（截止发布日期，2.4）是否仍会有仅限安全的版本？

Adobe也将继续对最新发行版本发布仅限安全的版本。 [引入新的仅用于安全保护的修补程序版本](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) DevBlog文章中概述了这些操作的过程。

## 什么是Quality Patches工具？

请参阅我们的支持知识库中的[Quality Patches Tool released： a new tool to self-service quality patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)文章。

## 谁应考虑使用此新策略？

这项新政策旨在为商家创造路径，从战略角度规划每年的Adobe Commerce开发成本，同时允许他们在这些战略周期中保持安全和关键质量。 那些关心其他一切的安全问题，并且通常对较旧、受支持线路的稳定性感到满意的商家也可以利用它。 商家可能会发现更容易规划和预算这些升级，因为它们将更容易预测。

## 商家是否仍应升级到最新系列？

最终，所有商户仍应优先考虑计划及时采用最新的Adobe Commerce产品。 新的仅限安全线路和QPT工具并非旨在替代商家的战略升级路线图；相反，它们为商家提供了规划升级路线图的灵活性，以及在无需实施整个升级的情况下快速响应安全/质量问题的方式。

## 如何获得非最新版本的受支持次要版本的质量修复？

将通过[Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patche)进行修复。

## 我如何获得最新产品线的质量修复？

作为季度更新的一部分，当前线路将具有质量。 在版本之间，如果您联系支持人员来获取最新行的修补程序，他们将通过QPT提供该修补程序。 然后，升级到包含该修复程序的版本后，将通过季度修补程序应用该版本。

## 对于不是最新版本的受支持的次要版本，将修复哪些类型的质量问题？

只有中断核心流程的主要质量问题才能在上一行(2.3)中修复并通过QPT交付。

## 对于不是最新版本的受支持次要版本，季度版本中是否会包含任何质量修复？

是的，作为仅安全线路的一部分，我们在该线路中发布了Adobe所谓的“热修复程序”，这些是影响Adobe Commerce应用程序的高度关键问题。

## 是否会同时提供安全改进和QPT？

仅限安全级别的线路将遵循季度发布计划，并以 — p1命名法发布。 示例2.3.6-p1. 质量将在发现并修复质量问题后临时发布，并将通过QPT提供。

## 如果我有质量问题，但在非最新行或QPT的支持次要版本中无法解决，我该怎么办？

前一条线路仅用于安全保护，这意味着主要好处是保持安全。 只有中断核心流的重大问题的修补程序才能通过QPT提供。

不影响核心流或具有解决方法的问题将仅在最新一行中修复。 Adobe鼓励那些既希望进行关键修复，也希望进行非关键修复的用户转到最新行。

## 如果商户在到达安全性支持终止之前仍使用仅安全线路，那么升级成本会更高还是更困难？

理论上，只要商户没有采用大量质量补丁，它们在开发时间方面的成本就应该是相等的。 如果商家发现他们需要或希望通过QPT工具获得多个修补程序，建议他们优先考虑升级到最新版本的Adobe Commerce。 如果采用大量质量补丁而不是升级到当前版本的Adobe Commerce，那么一旦安全专用线路终止支持，将增加升级的开发成本和复杂性。

## 为何要限制通过QPT提供的高质量补丁数量？

通过应用多个单独的质量修复，您可以使Adobe Commerce代码变得更加复杂。 当升级到最新版本行时，增加的复杂性可能会导致不可预测的更改。 因此，我们建议谨慎使用QPT，并且只将其用于最关键的修复。

## 技术栈栈的合规性如何？

在发布线的生命周期中，将更新各种技术栈栈(如PHP或Elasticsearch)，需要升级才能保持合规性。 我们会尽可能多地通知商家，这些商品即将推出。

注意：在2021年第2季度，我们将需要更新2.3.x系列上的PHP和Redis以保持合规性。 这将导致该行递增到2.3.7。有关详细信息，请参阅对Adobe Commerce 2.3.x版本行](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946)的DevBlog帖子[PHP 7.4支持。
