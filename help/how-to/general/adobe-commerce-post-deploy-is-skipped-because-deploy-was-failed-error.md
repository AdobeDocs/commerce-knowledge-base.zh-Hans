---
title: Adobe Commerce *已跳过部署后，因为部署失败*错误
description: 本文说明如何调查部署错误： *由于部署失败，已跳过部署后*
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# 已跳过Adobe Commerce *后期部署，因为部署失败*&#x200B;错误

本文说明如何调查部署错误： *已跳过部署后，因为部署失败*，此错误发生在部署到不同环境（例如升级）期间。

## 受影响的产品和版本

云基础架构上的Adobe Commerce [所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

部署失败并返回一般错误消息，因此不清楚如何解决错误。

## 原因

未确定 — 导致此错误消息的原因取决于已部署的代码和数据库。

## 如何调查部署错误

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

要获取用于确定实际原因的错误跟踪，请SSH到服务器并检查日志文件`var/log/install_upgrade.log`。
