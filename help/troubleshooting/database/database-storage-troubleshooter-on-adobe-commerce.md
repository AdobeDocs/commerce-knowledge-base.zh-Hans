---
title: Adobe Commerce上的数据库存储疑难解答
description: 对于Adobe Commerce上遇到数据库问题的客户，本文是一个故障排除工具。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状和配置，故障诊断程序将说明如何诊断数据库的空间和配置问题。
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Adobe Commerce上的数据库存储疑难解答

对于Adobe Commerce上遇到数据库问题的客户，本文是一个故障排除工具。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状和配置，故障诊断程序将说明如何诊断数据库的空间和配置问题。

## 步骤1 — 标识存在空间问题的目录 {#step-1}

+++**是否因空间不足而出现`/tmp`问题？**

这可以通过一系列症状来指示，包括`/tmp`装载已满、站点已关闭或无法通过SSH连接到节点。 您可能还会遇到诸如&#x200B;_设备(28)上已没有剩余空间_&#x200B;之类的错误。 有关因`/tmp`已满导致的错误列表，请查看[/tmp装入已满](/help/troubleshooting/miscellaneous/tmp-mount-full.md)。

还是由于缺少空间而导致`/data/mysql`问题？ 这也可能由各种症状指示，包括站点中断、客户无法将产品添加到购物车、与数据库的连接失败以及类似&#x200B;_SQLSTATE\[08S01\]的条码错误：通信链接失败： 1047 WSREP_。 有关因磁盘空间不足[!DNL MySQL]导致的错误列表，请参阅Adobe Commerce上云基础架构上的[[!DNL MySQL] 磁盘空间不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)。

如果不确定您是否存在磁盘空间问题并且您拥有New Relic帐户，请转到[New Relic基础架构监视主机页面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)。 从该位置，单击&#x200B;**存储**&#x200B;选项卡，将&#x200B;**图表显示**&#x200B;下拉列表从5个结果更改为20个结果，并在表中查找磁盘使用率在%图表或表中是否较高。 有关更多详细步骤，请参阅[New Relic Infrastructure Monitoring > Storage选项卡]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)。

如果您出现上述任何症状，请检查索引节点的状态，确保这不是由文件编号问题引起的。 为此，请在CLI/终端中运行以下命令：\
`df -ih`

IUse% > 90%吗？

a.是 — 这是由于文件过多所致。 查看在[磁盘空间不足时安全删除文件，云基础架构上的Adobe Commerce ](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-26889)中安全删除文件的步骤。 完成这些步骤后，请继续执行[步骤2](#step-2)。 如果要请求更多空间，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 检查空间。 在CLI/终端中运行`df -h | grep mysql`，然后运行`df -h | grep tmp`，以检查`/tmp`和`/data/mysql`目录中的磁盘空间使用情况。 继续执行[步骤3](#step-3)。

+++

## 步骤2 — 检查磁盘空间 {#step-2}

+++**检查磁盘空间使用情况？**

减少文件数后，在CLI/终端中运行`df -h | grep mysql`，然后运行`df -h | grep tmp`以检查`/tmp`和`/data/mysql`中的磁盘空间使用情况。 `/tmp`或`/data/mysql`的使用率是否大于70%？

a.是 — 继续执行[步骤3](#step-3)。
b.否 — 查询可能会耗尽可用存储。 这可能会使节点崩溃，从而终止查询并删除`tmp`文件。 在[!DNL MySQL] CLI中检查`SHOW PROCESSLIST;`的输出以查找可能导致问题的查询。 [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

## 步骤3 — 识别高使用率的目录 {#step-3}

+++**哪个目录的使用率超过70%？**

哪个目录的使用率超过70%？ `/tmp`或`/data/mysql`？

>[!NOTE]
>
>默认情况下，数据库tmpdir写入`/tmp`。 要检查您的数据库配置是否仍保留此默认值，请在[!DNL MySQL] CLI中运行以下命令： `SHOW VARIABLES LIKE "TMPDIR";`如果数据库tmpdir仍在写入`/tmp`，您将在“值”列中看到`/tmp`。

a. `/tmp` — 继续执行[步骤4](#step-4)。 \
b. `/data/mysql` — 继续执行[步骤5](#step-5)。

+++

## 步骤4 — 故障排除/tmp mount full {#step-4}

+++**疑难解答/tmp装载已满**

[对Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)进行/tmp装载完整故障诊断，向下滚动文章，并尝试解决方案和最佳实践。 然后在CLI/终端中运行`df -h | grep mysql`，然后运行`df -h | grep tmp`，以检查`/tmp`和`/data/mysql`目录中的磁盘空间使用情况\
  &lt; 70%已使用？

>[!NOTE]
>
>[Troubleshoot /tmp mount full for Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)中的解决方案是为未更改数据库tmpdir变量（默认写入`/tmp`）的商家设计的。 如果您更改了tmpdir值，则[Adobe Commerce的/tmp mount full疑难解答](/help/troubleshooting/miscellaneous/tmp-mount-full.md)中的说明将没有帮助。

答：是的，你已经解决了这个问题。 \
b.否 — [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

## 步骤5 — 检查默认值 {#step-5}

+++**检查默认值**

数据库配置可能不再为原始默认值。 通过在[!DNL MySQL] CLI `SELECT @@DATADIR;`中运行来查找数据库tmpdir配置。 如果输出`/data/mysql/`，则数据库tmpdir现在正在写入`/data/mysql/`。 在云基础架构上的Adobe Commerce上[[!DNL MySQL] 磁盘空间不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)中，按照以下步骤来尝试增加此目录中的空间。 然后在CLI/终端中运行`df -h | grep mysql`，然后运行`df -h | grep tmp`以检查`/data/mysql`和`/tmp`中的磁盘空间使用情况。\
  &lt; 70%已使用？

答：是的，你已经解决了这个问题。 \
b.否 — [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

[返回步骤1](#step-1)

## 相关阅读

* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
