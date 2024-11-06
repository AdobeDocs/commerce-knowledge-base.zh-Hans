---
title: “‘更新程序应用程序不可用’错误”
description: 本文介绍了在使用Web设置向导在本地更新/安装Adobe Commerce时，可能遇到的针对“更新程序应用程序不可用”问题的解决方案。
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# “更新程序应用程序不可用”错误

本文介绍了在使用Web设置向导在本地更新/安装Adobe Commerce时，可能遇到的针对“更新程序应用程序不可用”问题的解决方案。

## 问题

准备情况检查中会显示以下消息：

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## 受影响的产品/版本

* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x


## 解决方案

要解决此问题，请查看是否存在包含文件和子目录的`<magento_root>/update`目录。 否则，请参阅我们的开发人员文档中的[设置更新程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error)。
