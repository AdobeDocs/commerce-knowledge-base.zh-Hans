---
title: 配置NPM以便能够使用PWA Studio
description: '[渐进式Web应用程序(PWA) Studio](https://magento.github.io/pwa-studio/)是一个新项目，可用于Adobe Commerce on cloud infrastructure 2.3.x或更高版本上的cloud。 为了能够使用和安装PWA Studio，您需要将NPM包管理器版本设置为5.x或更高版本，以获取对Node.js 8.x的支持。此操作在“.magento.app.yaml”配置文件的“hooks：build”部分中完成。'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 配置NPM以便能够使用PWA Studio

[渐进式Web应用程序(PWA) Studio](https://magento.github.io/pwa-studio/)是一个新项目，可在Cloud Infrastructure 2.3.x或更高版本上用于Adobe Commerce。 为了能够使用和安装PWA Studio，您需要将NPM包管理器版本设置为5.x或更高版本，以获取对Node.js 8.x的支持。此操作在`hooks:build`配置文件的`.magento.app.yaml`部分中完成。

## 环境和技术

* 云基础架构上的Adobe Commerce 2.3.X
* 适用于Adobe Commerce的PWA

## 设置NPM版本：步骤

要设置所需的NPM版本，请在`.magento.app.yaml`配置文件中指定该版本。 请按照以下步骤操作：

1. 在本地开发环境中，找到`.magento.app.yaml`配置文件。
1. 使用纯文本编辑器或IDE打开文件进行编辑。
1. 在`hooks:build`部分中设置所需版本。 在以下示例中，配置设置为安装NPM v9.5.0，这是当前可用的最高版本（2019年2月4日）：

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >如果您想在应用程序中运行Node.JS，而不想仅在内部版本中运行，请添加以下命令以更改内部版本挂接：
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. 在文件中保存更改。
1. Git将编辑的文件推送到[集成环境](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)。

在Git将更新的YAML文件推送到环境后，更改将生效。

## 相关文档

* [应用程序配置：我们的Adobe Commerce on Cloud Infrastructure指南中的挂接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html)。
