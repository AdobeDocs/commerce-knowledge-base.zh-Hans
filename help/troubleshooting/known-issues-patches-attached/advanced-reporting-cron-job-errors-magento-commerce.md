---
title: 高级报告cron作业错误Adobe Commerce
description: 本文为Adobe Commerce中的高级报告cron作业问题提供了修补程序，如果客户尝试访问高级报告，可能会导致404错误。
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 高级报告cron作业错误Adobe Commerce

本文为Adobe Commerce中的高级报告cron作业问题提供了修补程序，如果客户尝试访问高级报告，可能会导致404错误。

## 受影响的产品和版本

Adobe Commerce（所有部署选项） 2.3.x

## 问题

客户尝试访问高级报告时收到404错误，并且与`analytics_collect_data job`关联的日志中存在错误。

## 兼容的Magento版本：

这些修补程序与以下Adobe Commerce版本兼容（但可能无法解决此问题）：

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)： Adobe Commerce（所有部署选项） 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)： Adobe Commerce（所有部署选项） 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)： Adobe Commerce（所有部署选项） 2.3.0

## **解决方案**

要解决此问题，请应用本文附带的相应修补程序。 要下载它，请单击以下链接：

* 下载[MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* 下载[MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* 下载[MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

要检查要使用的修补程序，请执行以下操作：

<ol><li>使用以下命令查看日志： <code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>根据您看到的错误，使用下表中的信息选择一个补丁程序。<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>错误</p>
</td>
<td class="wysiwyg-text-align-center">Patch</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL：运行cron作业{"exception"："[object] (RuntimeException(code：
  0)：运行cron作业时出错，网址为/srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php：327，
  TypeError（代码： 0）： substr_count()要求参数1为字符串，但给定null
  在/srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php：106)”}
  []</pre>或者<pre>report.ERROR： Cron Job analytics_collect_data有错误： substr_count()预期
  参数1为字符串，给定为null。 统计信息： {"sum"：0，"count"：1，"realmem"：0，"emalloc"：0，"realmem_start"：224919552，"emalloc_start"：216398384}
  [] []</pre>
<p> </p>
</td>
<td>应用<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>，清除缓存并等待24小时以使作业再次运行并重试。</td>
</tr>
<tr>
<td>
<p><em>无法打开文件/tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/.../</em></p>
</td>
<td>应用<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>，清除缓存并等待24小时以使作业再次运行并重试。</td>
</tr>
<tr>
<td><em>密码无效</em></td>
<td>应用<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>，清除缓存并等待24小时以使作业再次运行并重试。</td>
</tr>
</tbody>
</table>
</li></ol>

## 如何应用修补程序

解压缩文件并按照[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序中的说明操作。

## 相关阅读

[无法删除该文件。 警告！unlink：管理员没有此类文件或目录错误](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
