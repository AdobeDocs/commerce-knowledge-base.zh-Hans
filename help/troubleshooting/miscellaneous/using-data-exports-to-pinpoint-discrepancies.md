---
title: 使用数据导出来查明差异
description: 本文为排查MagentoBI数据中的差异提供了解决方案。 数据导出是一种有用的工具，可用于将MagentoBI数据与源数据进行比较，以查明报告中的数据差异，尤其是在[数据差异诊断核对清单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy)无法帮助您查明问题时。 本文将带您了解如何使用Data Exports查明数据差异的实际示例。
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 0%

---

# 使用数据导出来查明差异

本文为排查MagentoBI数据中的差异提供了解决方案。 数据导出是一种将MagentoBI数据与源数据进行比较的有用工具，可以查明报告中的数据差异，尤其是当[数据差异诊断核对清单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy)没有帮助您查明问题时。 本文将带您了解如何使用Data Exports查明数据差异的实际示例。

以这种分析为例：

![](assets/Exports_Discrepancies_1.png)

2014年11月出现了可疑的下降。 收入500,780.94美元？ 听起来不对。 您已确认源数据库中显示了更多的2014年11月收入，并仔细检查了是否正确定义了此报告中使用的&#x200B;**收入**&#x200B;指标。 似乎MagentoBI数据仓库中的数据不完整，可以使用“数据导出”来确认。

## 导出数据 {#export}

要开始使用此功能，请单击图表右上角的齿轮，然后单击下拉菜单中的原始导出选项。 这将为您提供图表背后数据的原始导出。

![](assets/Export_Discrepancies_5.gif)

在&#x200B;**原始数据导出**&#x200B;菜单中，您可以选择要导出的表以及要包含在导出中的列。 过滤器也可以应用于结果集。

在我们的示例中，此报表中使用的&#x200B;**Revenue**&#x200B;量度使用在&#x200B;**`orders`**&#x200B;表中定义的&#x200B;**order\_total**&#x200B;字段，并使用&#x200B;**date**&#x200B;作为其时间戳。 在我们的导出中，我们要包含2014年11月的所有&#x200B;**order\_id**&#x200B;值及其&#x200B;**order\_total** 。 **收入**&#x200B;量度不使用任何筛选器，但我们将为导出添加一个筛选器，以将结果集限制为仅2014年11月。

以下是本示例中原始数据导出菜单的外观：

![](assets/Exports_Discrepancies_2.png)

单击导出数据开始导出。 此时将显示一个窗口，其中包含导出的详细信息，包括状态。 准备导出需要几分钟的时间，现在可以开始对2014年11月的源数据进行类似提取，包括&#x200B;**日期、order\_id**&#x200B;和&#x200B;**order\_total** 。 我们将在Excel中打开此文件并保留它，因为我们将很快返回到它。

当“原始数据导出”窗口中出现“下载”按钮时，单击该按钮可下载包含CSV文件的zip文件。

![](assets/Export_Discrepancies_6.png)

此时，我们需要将所有数据放到一个工作表中，以找到问题。 我们将CSV文件(从MagentoBI导出)导入到包含源数据的其他Excel文件工作表中。

## 查明问题 {#pinpoint}

现在，所有数据都集中在一个位置，我们可以查找差异的来源。 比较每个工作表中的行数将有助于我们查明问题。 让我们更仔细地看一下每种情况。

### 两个工作表包含的行数相同

如果两个系统具有相同的行计数，且&#x200B;**收入**&#x200B;指标与源数据不匹配，则&#x200B;**order\_total**&#x200B;必须在某个位置关闭。 源数据库中的&#x200B;**order\_total**&#x200B;字段可能已更新，且MagentoBI未收到这些更改。

要确认这一点，请查看&#x200B;**order\_total**&#x200B;列是否正在重新检查。 前往Data Warehouse管理器并单击&#x200B;**`orders`**&#x200B;表。 您会看到“更改？”中列出了[重新检查频率](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) 列。 **order\_total**&#x200B;字段应设置为按预期更改频率重新检查；如果不更改，请将其设置为所需的重新检查频率。

### ![](assets/Export_Discrepancies_4.gif)

如果重新检查频率已正确设置，则表明存在其他问题。 请参阅本文末尾的[联系支持部分](#support)以了解后续步骤。

## 源数据库的行数比MagentoBI多 {#morerows}

如果源数据库的行数大于MagentoBI的行数，并且间隔大于在更新周期期间可预期接收的订单数，则可能存在连接问题。 这意味着MagentoBI无法从源数据库中提取新数据，这可能由于多种原因而发生。

导航到“连接”页面，并查看包含`order`表的数据源的状态：

1. **如果状态为“重新验证”**，则连接未使用正确的凭据。 单击进入连接，输入正确的凭据，然后重试。
1. **如果状态为“失败”**，则可能无法在服务器端正确设置连接。 连接失败通常是由于主机名不正确或目标服务器不接受指定端口上的连接造成的。单击连接并仔细检查主机名的拼写以及是否输入了正确的端口。 在服务器端，确保端口可以接受连接，并且防火墙具有允许的MagentoBI IP地址(54.88.76.97/32)。 **如果连接继续失败**，请参阅本文末尾的[联系支持部分](#support)以了解后续步骤。
1. **如果状态为Successful** ，则连接不是问题，需要联系RJ支持。 请参阅本文末尾的[联系支持部分](#support)以了解后续步骤。

## 源数据库的行数少于MagentoBI {#lessrows}

如果源数据库的行数少于MagentoBI，则可能正在从源数据库中删除行，并且MagentoBI不接收这些删除操作。 **&#x200B; [删除数据](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html)可能会导致不一致、更新时间延长以及后勤方面的一系列难题**，因此我们强烈建议您永远不要删除数据，除非它真的必要。

但是，如果从表中删除了行，请查看主键上的重新检查频率。 重新选中主键表示将检查表中是否包含已删除的行。

在Data Warehouse管理器中，主键列用键符号标记。 在我们的示例中，主键是&#x200B;**order\_id**&#x200B;列：

![](assets/Export_Discrepancies_3.png)

如果主键已设置为重新检查或从未从该表中删除行，则需要RJ支持来查明问题。 有关后续步骤，请参阅以下部分。

## 联系支持 {#support}

如果无法查明问题的根源，则需要在RJ支持中循环。 在提交票证之前，请执行以下操作：

* **如果源数据库和MagentoBI具有相同的行数**，并且重新检查频率设置正确，请在电子表格&#x200B;**中执行VLOOKUP，以找出哪些order\_id值在MagentoBI和源数据库之间具有不同的order\_total值。**&#x200B;在提交票证时包含这些值。
* **如果您的源数据库比MagentoBI多**&#x200B;行，并且连接显示为“成功”或继续失败，我们需要知道连接的名称和您看到的错误消息（如果有）。
* **如果源数据库的行数少于MagentoBI，则不会从表中删除**&#x200B;行，并且重新检查频率设置正确，请在电子表格&#x200B;**中执行VLOOKUP以查找哪些order\_id值在MagentoBI**&#x200B;中，而不是在源数据库中。 在提交票证时包含这些值。

## 相关阅读

* [数据差异诊断核对清单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy)
* [Adobe Commerce Intelligence服务策略](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/mbi-service-policies)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

