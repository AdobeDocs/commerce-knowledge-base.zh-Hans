---
title: 显示Adobe Commerce错误报告编号而不是Fastly 503错误
description: '默认情况下，Fastly会隐藏**503服务不可用**错误背后的所有Adobe Commerce错误。 要显示Adobe Commerce错误日志报告编号（以便能够在日志中找到它并查看错误详细信息），请打开网站，省略Fastly，步骤如下：'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 显示Adobe Commerce错误报告编号而不是Fastly 503错误

默认情况下，Fastly隐藏&#x200B;**503服务不可用**&#x200B;错误之后的所有Adobe Commerce错误。 要显示Adobe Commerce错误日志报告编号（以便能够在日志中找到它并查看错误详细信息），请打开网站，省略Fastly以下步骤：

1. 将应用程序的域和IP地址添加到本地计算机上的hosts文件中。
1. 清除浏览器缓存和Cookie（或切换到无痕模式）。
1. 再次打开您商店的网站以查看Adobe Commerce错误。

查看真实的Adobe Commerce错误和错误报告编号后，您可以在错误报告文件中按照以下步骤获取详细信息：

1. SSH连接到受影响的环境。 请参阅我们的开发人员文档中的[SSH到环境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)。
1. 找到`./var/report/{error_number}`文件。

## 将应用程序域和IP地址添加到hosts文件：详细步骤

1. 在本地计算机上的命令行中执行`nslookup`命令，检查存储区的服务器IP：
   * 专业体系结构用户（暂存和生产环境）：

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * 入门体系结构用户（所有环境）；专业体系结构用户（集成环境）：

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. 使用以下格式将商店域和应用程序服务器IP添加到本地计算机上的hosts文件中：

```
{server_IP} {store_domain}
```
