---
title: 运行“setup：static-content：deploy”deployed_version.txt问题
description: 本文修复了手动运行“setup：static-content：deploy”命令时“deployed_version.txt”不可写错误。
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# 运行`setup:static-content:deploy` deployed_version.txt问题

本文修复了手动运行`setup:static-content:deploy`命令时出现`deployed_version.txt`不可写错误。

## 问题

如果您遵循Adobe Commerce on cloud infrastructure建议以使用配置管理（并将静态资产生成移动到构建阶段以减少部署期间的网站停机时间），则在手动运行`setup:static-content:deploy`命令时可能会遇到以下错误：

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## 原因

我们优化了部署过程以减少停机时间，并创建了指向静态资产文件的符号链接，而不是拷贝这些文件。 静态资产的存储位置是只读的，这就是为什么您会收到上述错误消息。

我们强烈建议不要手动运行静态内容部署，因为所有资产都已生成，如果您手动执行此操作，则文件之间将没有区别（主题文件也是只读的，您不能更改它们），因此此类操作没有任何意义。

## 解决方案

如果您仍要运行静态内容部署，请删除`pub/static`目录中的符号链接，然后再次运行`setup:static-content:deploy`命令：

```
find pub/static/ -maxdepth 1 -type l -delete
```
