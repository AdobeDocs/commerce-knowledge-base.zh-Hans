---
title: 未找到修补程序的部署错误
description: “本文为您遇到错误*未找到下一个修补程序的问题提供了解决方案：MDVA-XXXXX、ACSD-XXXXX。 请检查‘状态’命令是否可用于当前Magento版本*。”
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 未找到修补程序的部署错误

本文提供了升级实例时部署失败并在部署日志中看到错误问题的解决方案： *未找到下一个修补程序： MDVA-XXXXX、ACSD-XXXXX。 请检查当前Magento版本*&#x200B;的这些修补程序的“状态”命令可用性。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。


## 问题

升级Adobe Commerce时遇到错误： *找不到下一个修补程序*。

## 原因

以前为旧版本应用的修补程序不适用于或不再适用于新版本。

## 解决方案

1. 在QUALITY_PATCH部分下检查您的`.magento.env.yaml`文件，例如，

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. 在[Quality Patches发行说明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)中查找修补程序ID，以检查每个修补程序ID是否可以应用于要升级的Adobe Commerce新版本。
1. 如果该修补程序不适用于要升级到的新版Adobe Commerce，请从`.magento.env.yaml`文件中删除修补程序ID。
1. 查看错误指示的所有修补程序ID后，推送更改并重新部署。

## 相关阅读

* 在Commerce on Cloud Infrastructure指南中[应用修补程序](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment)。
