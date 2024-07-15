---
title: 更新Adobe Commerce软件时，git pull origin开发失败
description: 本文修复了在运行“git pull origin develop”时无法更新Adobe Commerce软件的问题。
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 更新Adobe Commerce软件时，git pull origin开发失败

本文修复了在运行`git pull origin develop`时无法更新Adobe Commerce软件的问题。

## 详细信息

更新Adobe Commerce软件的步骤之一是通过运行以下程序来更新本地存储库：

```bash
$ git pull origin develop
```

可能会显示以下错误：

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

要查找哪些文件会被覆盖，请阅读邮件或输入：

```bash
git status
```

下一部分将讨论建议的解决方案。

### 建议的解决方案

您的解决方案取决于您是否刻意修改了Adobe Commerce文件系统中的文件。 有关更多信息，请参阅以下部分之一。

#### 您特意修改了文件

按常规方式手动解决冲突。 如果不确定要做什么，请查阅[GitHub帮助](https://help.github.com/)。

#### 您没有刻意修改任何文件

尝试以下任一操作：

* 如果您确定未修改任何文件，并且不介意删除或覆盖Adobe Commerce文件系统中的更改，请输入：

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  之后，继续执行Adobe Commerce更新的后续操作。

* GitHub配置设置可能会防止将来出现这些错误。 默认情况下，GitHub使用操作系统默认的行结束字符存储内容。 如果您使用的是Linux，但另一个协作者使用Windows提交了一个更改，则在您克隆或拉取时，GitHub会将Windows行结尾转换为Linux。 当实际上未进行任何更改时，这会使文件看起来像是发生了更改。

  要将GitHub配置为忽略行结尾，请在Git客户端中输入以下命令：

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  如果使用Windows，请输入：

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe不建议或认可任何特定的GitHub配置设置。 前面的只是建议。 有关详细信息，请参阅[GitHub帮助](https://help.github.com/)。

  继续Adobe Commerce更新的中断位置。
