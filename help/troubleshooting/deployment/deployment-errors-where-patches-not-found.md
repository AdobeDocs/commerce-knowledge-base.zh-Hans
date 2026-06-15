---
title: 在部署或手动应用程序期间未找到修补程序错误
description: 本文提供了解决出现以下问题的解决方案：错误*未找到下一个修补程序：MDVA-XXXXX、ACSD-XXXXX。 使用“状态”命令*检查这些修补程序在当前Magento版本中的可用性。
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: be0c72a1759ba172666c7c9409c65a1a388e3f11
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 在部署或手动应用程序期间未找到修补程序错误

本文提供了升级实例时部署失败并在部署日志中看到错误问题的解决方案： *未找到下一个修补程序： MDVA-XXXXX、ACSD-XXXXX。 使用“status”命令*&#x200B;检查这些修补程序在当前Magento版本中的可用性。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 问题

升级Adobe Commerce时遇到错误： *找不到下一个修补程序*。

## 原因

以前为旧版本应用的修补程序不适用于或不再适用于新版本。

已安装的Quality Patches Tool包(`magento/quality-patches`)已过期时，也可能会出现此问题。

例如：

用例1：
* QPT 1.1.71中最初可能提供了2.4.7-p9的修补程序
* 较新的QPT版本（例如1.1.72）以后可能会添加对2.4.7-p10的支持
* 如果客户将Commerce升级到2.4.7-p10，但安装了旧版QPT，则QPT可能无法识别2.4.7-p10存在兼容的修补程序变体

用例2：
* QPT 1.1.72中可能添加了修补程序
* 如果客户安装了旧版QPT，QPT将无法识别该修补程序存在

在这些情况下，应用修补程序可能会失败，并出现如下消息：

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

发生这种情况的原因是，安装的QPT版本无法将当前Commerce版本映射到修补程序的适用版本。

## 解决方案

此问题不限于通过`.magento.env.yaml`应用修补程序的部署。 在使用以下方式手动应用修补程序时，也可能会出现相同的基本问题：

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

例如：

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

在这种情况下，该修补程序不可用于运行命令环境中安装的Adobe Commerce版本。

1. 检查QUALITY_PATCHES部分下的`.magento.env.yaml`文件，例如，

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. 在[Quality Patches发行说明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)中查找修补程序ID，以检查每个修补程序ID是否可以应用于要升级的Adobe Commerce新版本。
1. 如果该修补程序不适用于要升级到的新版Adobe Commerce，请从`.magento.env.yaml`文件中删除修补程序ID。
1. 查看错误指示的所有修补程序ID后，推送更改并重新部署。

## 相关阅读

* 在Commerce on Cloud Infrastructure指南中[应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment)。

