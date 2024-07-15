---
title: 从数据库中删除失败的登录尝试
description: 本文介绍如何从Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure数据库中删除预先存在的失败登录凭据。 对于版本2.2.10+和2.3.3+，您只需要运行附加的脚本。 对于较旧版本2.3.0-2.3.2-p2，您需要应用修补程序以停止日志记录并运行附加的脚本以删除预先存在的失败登录凭据。
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# 从数据库中删除失败的登录尝试

>[!NOTE]
>
>本文已于2020年4月13日更新，添加了名为DB\_CLEANUP\_SCRIPT\_v2的新脚本。 请使用附加的DB\_CLEANUP\_SCRIPT\_v2脚本清除其他表中预先存在的失败登录数据。 即使之前运行过DB\_CLEANUP\_SCRIPT\_v2以帮助确保清理其他表，您仍需要使用DB\_CLEANUP\_SCRIPT\_v1。

本文介绍如何从Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure数据库中删除预先存在的失败登录凭据。 对于版本2.2.10+和2.3.3+，您只需要运行附加的脚本。 对于较旧版本2.3.0-2.3.2-p2，您需要应用修补程序以停止日志记录并运行附加的脚本以删除预先存在的失败登录凭据。

## **受影响的产品和版本**

* 此问题影响Magento Open Source、Adobe Commerce内部部署以及Cloud Infrastructure 2.2.x、2.3.x及更早版本上的Adobe Commerce。
* Adobe Commerce 1.x部署不受影响。

## 问题

2019年，向Adobe Commerce报告了以下错误：允许将失败的登录尝试记录到Adobe Commerce 2.3.x和2.2.x中的数据库。作为回应，Adobe Commerce在Adobe Commerce 2.3.3和2.2.10（2019年10月发布）中包含了此问题的修复。 虽然针对该错误的修复已停止记录失败的登录尝试，但在更新到这些当前版本之前收集的信息可能仍然存在。 此最新修复会清除之前记录的登录尝试信息（如果有）。   在[常见漏洞和暴露](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118)中描述并跟踪了CVE-2019-8118。

## 解决方案

是需要使用附加的脚本和修补程序，还是只需要使用脚本，这取决于您的Adobe Commerce版本：

**Adobe Commerce和Magento Open Source版本2.3.0-2.3.2-p2**

对于这些版本，必须应用修补程序并运行附加的数据库清理脚本，以结束连续日志记录并消除日志。

1. 运行编辑器修补程序以停止日志记录。 此修补程序已附加到文章。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)。 有关如何应用修补程序的说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

1. 现在，运行脚本以清除预先存在的失败登录尝试的数据库。 此脚本已附加到文章。 要下载它，请向下滚动到文章结尾并单击文件名，或单击以下链接[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)。

有关说明，请参阅&#x200B;[**如何运行脚本**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script)&#x200B;部分。

**Adobe Commerce和Magento Open Source版本2.3.3及更高版本/2.2.10及更高版本**<br>
仅对于这些版本，请运行以下脚本以清除旧日志（之前通过2019年10月发布的修复程序终止了这些版本的日志记录）。 此脚本已附加到文章。 要下载它，请向下滚动到文章结尾并单击文件名，或单击以下链接[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)。

有关说明，请参阅我们的支持知识库中的&#x200B;[**如何运行脚本**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script)&#x200B;部分。

**如何运行脚本**

请按照以下说明运行脚本：

1. 将`DB_CLEANUP_SCRIPT_v2.php`放在Adobe Commerce或Magento Open Source安装的根目录中（与包含`app/bootstrap.php`的应用程序位于同一目录中）。
1. 在终端`php DB_CLEANUP_SCRIPT_v2.php`中运行此命令，它将开始数据库清理过程。

如果在运行脚本时遇到任何问题，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)或发送电子邮件至[security@magento.com](mailto:security@magento.com)。

**附加文件**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
