---
title: 用于防御依赖项混淆攻击的编辑器插件
description: 本文介绍了有关为依赖项混淆攻击发布的编辑器插件的信息以及有关避免错误的建议。 Composer插件随Adobe Commerce 2.4.3版的发布引入，以保护Adobe Commerce商家免受依赖项混淆攻击。
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 用于防御依赖项混淆攻击的编辑器插件

本文介绍了有关为依赖项混淆攻击发布的编辑器插件的信息以及有关避免错误的建议。 Composer插件随Adobe Commerce 2.4.3版的发布引入，以保护Adobe Commerce商家免受依赖项混淆攻击。

## 受影响的产品和版本

* Adobe Commerce 2.4.3和未来版本（所有部署方法）

## 问题

在编辑器安装/更新期间，通过编辑器插件`magento/composer-dependency-version-audit-plugin`在`composer.json`中定义的至少一个直接或间接依赖项检测到活动依赖项混淆攻击的可能情况。

<u>重现步骤</u>：

安装/更新编辑器时，如果编辑器插件检测到潜在的依赖项混淆攻击，则会停止该进程。 在这种情况下，编辑器安装/更新将失败，并出现类似于以下内容的错误消息：

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## 原因

依赖关系混淆攻击允许通过跟踪依赖关系管理器（例如PHP的编辑器）从公共源下载恶意包，而不是从专用存储库下载原始包，在服务器上远程执行任意代码。

如果攻击者能够保持原始包的功能，甚至可能检测不到此类攻击。

如果某个包只能通过专用存储库获得，但未在公共存储库中注册，则攻击者可以攻击该漏洞。 然后，攻击者会将同名的包上载到公共存储库，并赋予其比私有存储库更高的版本。 依赖项管理器随后将比较私有包和公开可用包的版本，并将从公共存储库中选择最高的包。 然后，依赖关系管理器下载的恶意代码将以与应用程序代码相同的权限执行。

## 解决方案

### Recommendations对商家

* 请认真对待插件停止编辑器安装/更新时显示的错误消息，如果您发现可能损坏的包，请联系扩展开发人员。
* 您仍然可以从Marketplace或其他受信任的专用存储库使用包的安全版本安装Adobe Commerce。
* 将composer.json中所需的包版本更改为Marketplace中的确切版本，以继续安装/更新编辑器。

### 扩展开发人员的期望

* 无法确定插件的包（如果来自公共存储库）是否已被破坏。 该插件将检测packagist.org上包的公共版本的版本何时高于私有存储库（如[repo.magento.com](https://repo.magento.com)）中的可用版本。 我们强烈建议扩展开发人员避免此类情况，并且不要公开发布比[repo.magento.com](https://repo.magento.com)提供的版本更新的版本。
* Adobe Commerce明白，市场审查流程可能会延迟扩展的发布，但是该流程旨在保护商家的安全，并帮助扩展开发人员发现他们可能错过的意外错误。
