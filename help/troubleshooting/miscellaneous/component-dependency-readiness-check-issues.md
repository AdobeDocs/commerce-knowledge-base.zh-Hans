---
title: 组件依赖项就绪检查问题
description: 本文提供了组件依赖关系冲突的解决方案。
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 组件依赖项就绪检查问题

本文提供了组件依赖关系冲突的解决方案。

## 解决组件依赖关系冲突 {#resolve-component-dependency-conflicts}

我们建议您按照显示的顺序尝试以下解决方案：

1. [冲突的依赖项](#trouble-depend-conflict)
1. [文件系统权限问题](#trouble-depend-permission)
1. [组件依赖关系检查状态从不更改](#trouble-depend-state)

### 冲突的依赖项 {#trouble-depend-conflict}

如果编辑器无法确定要安装或更新哪些组件，则会显示消息&#x200B;*我们发现冲突的组件依赖项*。 要解决组件依赖性问题，您应该成为完全了解编辑器如何工作的技术人员。

以下是示例失败消息：

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>您看到的消息可能会有所不同。

请参阅支持知识库中解决方案](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md)的[冲突的组件依赖项。

## 文件系统权限问题 {#trouble-depend-permission}

如果Adobe Commerce文件系统所有者无权写入Adobe Commerce文件系统上的目录，则会显示一条与以下内容类似的消息：

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

请确保按照开发人员文档中的[所有权和权限概述](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html)一文中所述设置文件系统权限。

## 组件依赖关系检查状态从不更改 {#trouble-depend-state}

在某些情况下，组件依赖关系检查的状态不会更改，甚至在您尝试更正问题后也是如此。 在这种情况下，您可以删除或重命名名为`<magento_root>/var/.update_cronjob_status`和`<magento_root>/var/.setup_cronjob_status`的文件，然后再次尝试运行组件管理器。

重命名或删除这些文件会强制组件管理器再次运行检查。
