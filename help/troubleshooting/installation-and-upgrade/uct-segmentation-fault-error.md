---
title: 升级兼容性工具错误疑难解答
description: 本文介绍在使用升级兼容性工具时可能遇到的错误，并提供修复这些错误的解决方案，以便您能够成功执行该工具。
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 升级兼容性工具错误疑难解答

本文介绍在使用升级兼容性工具时可能遇到的错误，并提供修复这些错误的解决方案，以便您能够成功执行该工具。

## 受影响的产品和版本

* [升级兼容性工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html)与2.3.0以后的Adobe Commerce版本兼容。

## 分段错误

<u>原因</u>：

当两个模块具有相同的名称时，升级兼容性工具显示分段错误错误。

<u>解决方案</u>：

要避免出现此错误，建议将模块的路径指定为参数：

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> 如果代码库在方法之间包含循环依赖关系，则升级兼容性工具可能无法分析代码库。

## 输出为空

<u>重现步骤</u>：

1. 如果运行此命令后：

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. 唯一输出为`Upgrade compatibility tool`：

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>原因</u>：

可能的原因是PHP内存限制。

有两种可能的解决方案可避免此PHP内存限制。

<u>解决方案1</u>：

通过将`memory_limit`设置为`-1`覆盖内存限制：

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION`是您要与Adobe Commerce实例进行比较的目标Adobe Commerce版本。

<u>解决方案2</u>：

添加`-m`选项允许升级兼容性工具独立分析每个特定模块，以避免在Adobe Commerce实例中遇到两个具有相同名称的模块。

此命令选项还允许升级兼容性工具分析包含多个模块的文件夹：

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

有关命令行界面选项的更多信息，请参阅[在命令行界面中运行工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html)页。
