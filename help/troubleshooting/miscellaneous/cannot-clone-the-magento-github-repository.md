---
title: 无法克隆MagentoGitHub存储库
description: 本文修复了无法克隆MagentoGitHub存储库的问题。
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# 无法克隆MagentoGitHub存储库

本文修复了无法克隆MagentoGitHub存储库的问题。

## 详细信息 {#detail}

错误类似于以下内容：

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## 解决方案 {#solution}

将SSH密钥上传到GitHub，如[GitHub帮助页面](https://help.github.com/articles/generating-ssh-keys)中所述。
