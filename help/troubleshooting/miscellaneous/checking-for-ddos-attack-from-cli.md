---
title: 检查来自CLI的DDoS攻击
description: 本文介绍了如何尝试从服务器的命令行界面(CLI)检查分布式拒绝服务(DDoS)攻击的问题。
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# 检查来自CLI的DDoS攻击

本文介绍了如何尝试从服务器的命令行界面(CLI)检查分布式拒绝服务(DDoS)攻击的问题。

## 受影响的产品和版本

* Adobe Commerce，所有版本
* Magento Open Source，所有版本

## 问题

您的网站速度较慢，并且除CLI外，您无权访问任何其他分析应用程序工具来检查潜在DDoS攻击。 DDoS攻击的症状可能会因网络配置、使用的软件等不同而有很大差异。

但是，建议您使用专门为帮助识别DDoS攻击而设计的分析软件产品。

## 原因

导致网站速度缓慢的原因有多种，包括服务器性能缓慢、CPU使用率较高或脚本、代码或廉价硬件配置错误。 有时可能是由于DDoS攻击造成的。 要检查DDoS攻击，您需要检查的两个基本工具是Adobe Commerce日志和CLI。

同样需要注意的是，使用专门用于识别DDoS攻击的软件，对您的调查非常有用。

## 解决方案步骤

1. 检查Adobe Commerce日志，查看是否发生了DDoS攻击以外的其他攻击。 有关更多信息，请参阅我们的开发人员文档中的以下文章：
   * [Adobe Commerce和Magento Open Source日志位置](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * 云基础架构上的[Adobe Commerce日志位置](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. 使用`netstat`命令开始使用CLI检查您当前所有的Internet连接： `netstat -na`。 这会显示与服务器的所有活动已建立连接。 在这里，您可能会注意到来自同一IP地址的连接过多。
1. 要进一步将已建立的连接结果缩小到仅连接端口80（网站的http端口）的连接，以便从一个IP地址或IP地址组对过多连接进行排序和识别，请使用以下命令： `netstat -an | grep :80 | sort`。 您可以对端口443上的https重复相同的命令： `netstat -an | grep :443 | sort`。 另一个选项是将原始命令同时扩展到端口80和443： `netstat -an | egrep ":80|:443" | sort`。
1. 要查看服务器上是否出现了许多活动的`SYNC_REC`，请使用以下命令：     `netstat -n -p|grep SYN_REC | wc -l`     该值通常小于5，但对于DDoS攻击，该值可能会高得多，不过对于某些服务器，较高的值可能是正常情况。
1. 要列出发送`SYNC_REC`状态的所有IP地址，请使用命令： `netstat -n -p | grep SYN_REC | sort -u`。
1. 要进一步列出发送`SYNC_REC`状态的所有唯一IP地址，请使用命令： `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`。
1. 您还可以使用`netstat`命令计数和计算每个IP地址与您的服务器建立的连接数： `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`。
1. 要列出连接到服务器的UDP或TCP协议连接的计数，请使用命令： `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`。
1. 要检查已建立的连接，而不是仅检查所有连接，并显示每个IP地址的连接计数，请使用命令： `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`。
1. 要显示按端口80的IP地址列出的连接计数，请使用命令： `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`。

确保有人对您发现的数据进行适当的分析，以确定您实际上是否遭受了DDoS攻击。 在上述步骤中使用服务器CLI中的`netstat`命令将帮助您分析是否遇到DDoS攻击，但使用专门为帮助识别DDoS攻击而设计的软件分析产品以及适当的分析是识别DDoS威胁的最佳工具。

如果您发现自己受到DDoS攻击，则可以采取的步骤取决于您的网络配置以及DDoS攻击是如何发生的，但一般建议是联系您的ISP，为您的服务器获取新的IP地址，和/或咨询熟练处理DDoS问题的IT专业人员，以分析您的具体情况并提出建议。

## 我们的开发人员文档中的相关阅读：

* [DDoS保护](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [使用CLI命令](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* 适用于Commerce的[Cloud CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
