---
title: Composer install命令覆盖.gitignore文件、Adobe Commerce
description: 本文为当Adobe Commerce上的编辑器在cloud infrastructure 2.4.2-p1和2.3.7上覆盖跟踪的“.gitignore”文件提供了一个解决方案。
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# Composer install命令覆盖.gitignore文件、Adobe Commerce

本文提供了一个解决方案，用于在Adobe Commerce上由编辑器在Cloud Infrastructure 2.4.2-p1和2.3.7上覆盖跟踪的`.gitignore`文件。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.4.2-p1和2.3.7。

## 问题

运行composer install命令时正在覆盖`.gitignore`文件。

<u>重现步骤</u>：


1. 为工作区创建一个空目录。
1. 在根目录中运行此命令：

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \#或2.3.7

1. 然后运行以下命令：
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. 已提交到存储库的`git commit -m "Init"` #个文件
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>预期的结果</u>：

`.gitignore`未被编辑器覆盖。

<u>实际结果</u>：

每次运行composer时都会覆盖`.gitignore`。

## 解决方案

要保留您的自定义`.gitignore file`，您需要在`magento-deploy-ignore`分区中忽略它。

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## 相关阅读

* [跟踪的.gitignore文件已被编辑器覆盖！](https://github.com/magento/magento2/issues/32888) 在Magento2 GitHub中。
