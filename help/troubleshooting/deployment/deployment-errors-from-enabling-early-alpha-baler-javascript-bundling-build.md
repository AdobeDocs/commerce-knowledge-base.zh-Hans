---
title: 启用早期alpha包模块时出现部署错误
description: 商家在生产环境中使用Baler模块时遇到部署错误，因为该功能当前处于早期Alpha开发阶段。
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 启用早期alpha包模块时出现部署错误

商家在生产环境中使用Baler模块时遇到部署错误，因为该功能当前处于早期Alpha开发阶段。

>[!WARNING]
>
>早期的alpha Baler Javascript捆绑未准备好用于生产，使用时需要自行承担风险。

## 受影响的产品和版本

* 云基础架构2.3.x和2.4.x上的Adobe Commerce。
* Adobe Commerce内部部署2.3.x和2.4.x。

## 问题

我们不建议商家在生产环境中使用Baler模块，因为它当前处于早期alpha开发阶段。 使用此配置文件可能会导致部署错误。

<u>重现步骤</u>：

1. 商家尝试在`.magento.env.yaml`文件的构建阶段中插入&#x200B;**SCD\_USE\_BALER**&#x200B;变量，该变量将启用Baler Javascript捆绑包。
1. 商家还将Baler编辑器依赖项`"magento/module-baler": "1.0.0-alpha"`添加到`composer.json`的`require`部分。

<u>预期的结果</u>：

部署成功。

<u>实际结果</u>：

商家在静态内容部署阶段的云上的部署日志中看到以下错误消息： `<project home>/var/log/cloud.log`

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## 原因

Baler模块目前处于早期alpha开发阶段，并且Baler扩展安装过程复杂。

## 解决方案

您可以在[Github/Baler/Baler/Alpha快速入门](https://github.com/magento/baler/blob/master/docs/ALPHA.md)上查看现有MagentoAlpha文档。 但是，它还没有准备好用于生产，使用它时您将自行承担风险。 为此，建议您使用Adobe Commerce的内置捆绑包（基本捆绑包）来合并或捆绑多个Javascript (JS)文件，以便优化文件。

* 您可以在管理员中启用合并或捆绑（合并和捆绑无法同时启用）： **存储** > **设置** > **配置** > **高级** > **开发人员** > **JavaScript设置**。
* 您还可以从以下命令行启用Adobe Commerce的内置捆绑包（基本捆绑包）： `php -f bin/magento config:set dev/js/enable_js_bundling 1`

要了解更多信息，请参阅云基础架构上的Adobe Commerce和Adobe Commerce内部部署上的[CSS和Javascript文件优化](https://support.magento.com/hc/en-us/articles/360044482152)。
