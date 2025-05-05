---
title: 部署失败，并显示“构建项目时出错：构建挂接失败，状态代码为1”
description: 本文讨论了Adobe Commerce云基础架构问题的原因和解决方案，该问题导致部署过程的构建阶段失败，并且错误消息概述为：*“错误构建项目：构建挂接失败，状态代码为1”*。
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 6a880a57c6cafb34fa51706f7bab1e23310bcef7
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# 部署失败，并显示“构建项目时出错：构建挂接失败，状态代码为1”

本文介绍了Adobe Commerce on cloud infrastructure问题的原因和解决方案，该问题导致部署过程的构建阶段失败，并且错误消息摘要为： *“错误构建项目：构建挂接失败，状态代码为1”*。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

<u>重现步骤</u>：

手动触发部署，或通过执行环境的合并、推送或同步来触发部署。

<u>预期的结果</u>：

已成功完成部署。

<u>实际结果</u>：

1. 构建阶段失败，并且整个部署过程陷入停滞。
1. 在部署错误日志中，错误消息结尾为： *&quot;构建项目时出错：构建挂接失败，状态代码为1。 已中止生成“。*”

## 原因

环境构建失败的原因有多种。 通常，在部署日志中，您会看到一条较长的错误消息，其中第一部分将更具体说明原因，结论为&#x200B;*&quot;构建项目时出错：构建挂接失败，状态代码为1。 已中止生成“。*”

详细了解第一个问题特定部分将有助于您识别问题。 下面是一些最常见的问题，下一部分将为其提供解决方案：

* 没有可用的存储空间。
* ECE-Tools配置不正确。
* 您尝试应用的修补程序与Adobe Commerce版本不兼容，或者与应用的其他修补程序或自定义设置冲突。
* 自定义模块代码问题导致无法成功构建。

## 解决方案

* 检查以确保有足够的存储空间。 有关如何检查可用空间的信息，请参阅[使用CLI检查云环境上的磁盘空间](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md)一文。 您可以考虑清除日志目录和/或增加磁盘空间。
* 确保ECE-Tools配置正确。
* 检查问题是否由修补程序引起。 解决冲突或联系[Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。 有关详细信息，请参阅下文。
* 检查是否是由自定义扩展导致的问题。 解决冲突或联系扩展开发人员以获取解决方案。

以下段落提供了一些更多详细信息。

### 清理日志和/或增加空间

要考虑清理的目录：

* `var/log`
* `var/report`
* `var/debug/`
* `var`

有关如何在云基础架构的Adobe Commerce上增加磁盘空间入门计划架构的详细信息，请参阅[增加云上集成环境的磁盘空间](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)。 相同的说明可用于在云基础架构上增加Adobe Commerce的空间。专业规划架构集成环境。 对于Pro Production/Staging，您需要向[Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)提交票证，并请求增加磁盘空间。 但受Platform监控。 但通常情况下，您无需在Pro体系结构的测试/生产中处理此事宜，因为Adobe Commerce会为您监控这些参数，并提醒您和/或根据合同采取行动。

### 确保ECE工具配置正确

1. 确保在`magento.app.yaml`文件中正确定义了生成挂接。 如果您在Adobe Commerce 2.2.X上，则构建挂接应定义如下：

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   请参考[升级到ece-tools](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package)一文。

1. 通过运行以下命令，确保`composer.lock`文件中存在ECE-tools软件包：

   ```bash
   grep '"name": "magento/ece-tools"' composer.lock
   ```

   如果指定这两个参数，则响应将类似于以下示例：

   ```bash
   "name": "magento/ece-tools", "version": "2002.0.20",
   ```

请参阅[升级到ece-tools](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package)文章以供参考。

### 修补程序是否导致该问题？

如果所应用的修补程序阻止环境成功构建，则会在部署日志中看到与以下内容类似的内容：

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

这些错误消息表示您尝试应用的修补程序是为其他Adobe Commerce版本创建的，或者与您的自定义项或以前应用的修补程序冲突。 尝试解决冲突或联系[Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 扩展是否导致了问题？

如果自定义扩展阻止环境成功构建，您将会看到部署日志中提到的自定义模块名称，以及此模块导致的特定冲突。 解决冲突或联系扩展开发人员以获取解决方案。

### 确保应用更改

提交并推送更改。 这将自动触发部署。
