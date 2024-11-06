---
title: 集成环境增强请求 — Pro和Starter
description: 如果您是Adobe Commerce on cloud infrastructure Pro计划架构客户，并且当前使用标准大小的集成环境，或者您是Adobe Commerce on cloud infrastructure入门计划架构客户，并且当前使用标准大小的暂存环境并希望获得更多动力，您可以请求升级到增强型集成环境，该环境可提供大约四倍的性能。 本文将Pro客户和Starter客户的说明分开。
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 集成环境增强请求 — Pro和Starter

如果您是Adobe Commerce on cloud infrastructure Pro计划架构客户，并且当前使用标准大小的集成环境，或者您是Adobe Commerce on cloud infrastructure入门计划架构客户，并且当前使用标准大小的暂存环境并希望获得更多动力，您可以请求升级到增强型集成环境，该环境可提供大约四倍的性能。 本文将Pro客户和Starter客户的说明分开。

>[!NOTE]
>
> 升级到增强型集成可能无法解决所有性能问题，因为它将取决于安装的总资源要求，包括第三方集成或自定义。
>
> 您还需要确保遵循最佳实践，以在集成环境中获得最佳性能，即使这也可能不是最终解决方案。 有关指导，请参阅以下文档： 《Commerce on Cloud Infrastructure指南》中的[专业体系结构](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)和[入门体系结构](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)。

## Pro

1. 如果您使用Pro，若要升级，必须将集成分支的数量减少到两个（**主集成分支包含在总计**&#x200B;中）。 **注意：请勿在此总计中计算主分支。 主分支不被视为集成分支。**&#x200B;按照开发人员文档中的[使用Cloud Console管理分支](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html)中的步骤进行操作。
1. 商家需要[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求升级到增强集成环境，使用联系原因“*请求云配置更改*”。
1. Adobe客户工程团队会确认集成环境的数量，并开始进行更改。
1. 升级完成后，贸易商将在票证中收到通知。
1. 商家重新部署集成环境。 按照开发人员文档中的[合并分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)中的步骤操作。 *注意*：运行时将自动进行部署： <pre>git push origin <branch-name></pre>

性能提高表示成功升级到增强集成环境。

**备注**：

* 标准大小和增强大小是唯一可用的两种大小。
* 给定存储的所有集成环境的大小相同 — 无法单独调整大小。
* 如果您需要两个以上的增强集成环境，请咨询您的Adobe客户团队。

## 起始者

1. 入门计划不能有任何集成分支：商家必须删除集成环境并仅离开暂存环境。 按照开发人员文档中的[使用Cloud Console管理分支](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html)中的步骤进行操作。 可用的环境数将减少到最多允许一个集成环境。
1. 商家需要[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求升级到增强集成环境，使用联系原因&#x200B;*“请求云配置更改”* - **您的暂存环境是一个命名的集成环境**。
1. Adobe客户工程团队会确认集成环境的数量，并开始进行更改。
1. 升级完成后，贸易商将在票证中收到通知。
1. 商家重新部署集成环境。 按照开发人员文档中的[合并分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)中的步骤操作。 *注意*：运行时将自动进行部署： <pre>git push origin <branch-name></pre>

性能提高表示成功升级到增强集成环境。

**备注**：

* 标准大小和增强大小是唯一可用的两种大小。
* 给定存储的所有集成环境的大小相同 — 无法单独调整大小。
* 如果您需要暂存环境以外的集成环境，请咨询您的Adobe客户团队。
* 如果购买是在2020年9月17日之后，则由于集成环境的扩大，此增强功能将不适用。
