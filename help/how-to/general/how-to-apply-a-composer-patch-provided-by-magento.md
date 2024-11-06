---
title: 如何应用Adobe提供的编辑器修补程序
description: 本文说明如何在本地Adobe Commerce、云基础架构和Magento Open Source上为Adobe Commerce应用编辑器修补程序。
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 如何应用Adobe提供的编辑器修补程序

本文说明如何在本地Adobe Commerce、云基础架构和Magento Open Source上为Adobe Commerce应用编辑器修补程序。

>[!WARNING]
>
>我们强烈建议先在暂存/集成环境中应用和测试修补程序，然后再将其应用于生产。 我们建议您在进行任何操作之前先进行备份。

## 如何在云基础架构上为Adobe Commerce应用编辑器修补程序 {#cloud}

1. 如果项目根目录中没有名为`m2-hotfixes`的目录，请创建一个。
1. 将`%patch_name%.composer.patch`文件复制到`m2-hotfixes`目录。
1. 添加、提交和推送代码更改：

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

有关将修补程序应用到云项目的其他信息，请参阅我们的开发人员文档中的[应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

### 如何为Adobe Commerce内部部署和Magento Open Source应用编辑器修补程序 {#commerce}

1. 将修补程序上传到Adobe Commerce内部部署或Magento Open Source根目录。
1. 运行以下SSH命令：

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   （如果上述命令不起作用，请尝试使用`-p2`而不是`-p1` ）

1. 要使更改生效，请在&#x200B;**系统** > **缓存管理**&#x200B;下的管理员中刷新缓存。
