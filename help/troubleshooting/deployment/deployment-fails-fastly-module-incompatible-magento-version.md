---
title: 部署失败Fastly模块不兼容的Adobe Commerce版本
description: '更新时间：2019年2月29日'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 部署失败Fastly模块不兼容的Adobe Commerce版本

更新日期： 2019年2月29日

本文修复了由于Fastly模块与当前Adobe Commerce版本不兼容而导致部署失败的情况。

**问题：**&#x200B;在新提交和推送后部署失败，错误消息如下所示：

>\[Exception\]警告：缺少Fastly\\Cdn\\Plugin\\...的参数3，该参数在/app/vendor/magento/framework/Interception/Interceptor.php中调用，并在/app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php中定义……

**原因：**&#x200B;在Fastly模块v1.2.79中进行向后不兼容的更改。

**解决方案（临时）：**&#x200B;将Fastly模块升级到版本1.2.82或更高版本，并在Commerce管理中上传新的VCL。 然后，提交并推送更改以触发成功的部署。

## 受影响的版本

* Adobe Commerce内部部署2.1.X
* 云基础架构上的Adobe Commerce 2.1.X
* Fastly模块1.2.79

## 问题

当您提交更改并将其推送到集成、生产或暂存环境时，通常下一步是触发部署过程。 此操作在Adobe Commerce on cloud infrastructure版本中自动完成，并在Adobe Commerce内部部署中手动完成。

部署可能会失败，并出现以下错误消息：

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

如果您在云基础架构解决方案上使用Adobe Commerce，您将在[部署日志](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/test/log-locations)中看到此错误消息。 对于Adobe Commerce内部部署，您将在命令行中看到错误。

## 原因

问题是由于Fastly模块v1.2.79中的向后不兼容更改引起的。

## 解决方案

将Fastly模块升级到版本1.2.82或更高版本。

为此，请执行以下步骤：

1. 执行以下命令之一：
   * 如果Fastly模块包含在magento-cloud-metapackage中：    <pre>编辑器更新magento/magento-cloud-metapackage</pre>
   * 如果Fastly模块是单独安装的(例如，如果您使用的是本地Adobe Commerce，而不是云版本) <pre>编辑器更新fastly/magento2</pre>
1. 提交并推送更改，如果未自动完成，则触发部署过程。
1. 在管理员中，[将新VCL上传到Fastly](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets)。
