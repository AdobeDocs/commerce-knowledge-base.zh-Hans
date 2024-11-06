---
title: Adobe Commerce的Magento Order Management系统(OMS)超时
description: 针对Adobe CommerceMagento Order Management系统(OMS)由于MOM在尝试回调时超时，导致无法使用ngrok向MOM注册本地安装的微服务的问题，提出了一种解决方案。
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Adobe Commerce的Magento Order Management系统(OMS)超时

针对Adobe CommerceMagento Order Management系统(OMS)由于MOM在尝试回调时超时，导致无法使用ngrok向MOM注册本地安装的微服务的问题，提出了一种解决方案。

## 受影响的产品和版本

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>免责声明： Adobe Commerce不推荐也不认可任何用于建立隧道的特定工具。 前面的只是建议。 有关详细信息，请参阅[ngrok文档](https://ngrok.com/docs)。

## 问题

<u>重现步骤</u>

1. 在本地环境中安装Adobe Commerce。
1. 设置ngrok以创建一个通道来公开您的本地服务器。
1. 尝试[连接到OMS](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)。

<u>预期的结果</u>

已成功建立连接。

<u>实际结果</u>

尝试回调到登录URL时，MCOM似乎超时。

## 原因

超时的可能原因之一是服务器的地理位置太远，并且连接耗时过长。

## 解决方案

在启动ngrock时添加一个指定区域的参数。 如下所示：

```bash
./ngrok http 80 -region eu
```

默认区域为美国。 查看[所有可能的值](https://ngrok.com/docs#config_region)。
