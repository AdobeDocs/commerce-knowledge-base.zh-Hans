---
title: Adobe Commerce支持知识库开始接受投稿
description: 从6月15日开始，Adobe Commerce支持知识库团队开始通过[magento/知识库](https://github.com/magento/knowledge-base) GitHub存储库接受外部Adobe Commerce社区的直接编辑和新文章投稿！
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce支持知识库开始接受投稿

从6月15日开始，Adobe Commerce支持知识库团队开始通过[magento/知识库](https://github.com/magento/knowledge-base) GitHub存储库，接受外部Adobe Commerce社区的直接编辑和新文章投稿！

是否注意到我们的一篇文章中有打字错误，或者故障排除步骤不完整？
您现在可以自己修复它并获得贡献点数！

## Contribute

我们欢迎各种投稿，从较小的拼写错误更正到完整的故障排除文章。 向此存储库投稿可以获得奖励积分，与向Adobe Commerce代码和我们的开发人员文档投稿类似。 有关详细信息，请参阅[贡献奖励积分](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md)。

### 常规贡献流

1. 创建分支存储库。
1. 对分支存储库进行编辑。
1. 将拉取请求(PR)提交到此存储库。
1. 运行测试：
   * AdobeCLA — 确保已签署Adobe开放Source参与者许可协议。
   * Markdown Linting测试 — 确保Markdown语法正确。
   * 文件结构验证测试 — 确保根据[必需的文件结构](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure)完成提交。
1. PR审批流程：
   1. 支持知识库(KB)作者可在几天的时间范围内查看PR并添加标签。
   1. 知识库编写器可以批准/拒绝/请求更改。
   1. 如果获得批准，知识库作者会添加与PR中提供的输入级别对应的标签，内部主题专家(SME)将审阅PR。
   1. SME可以批准/拒绝/请求更改。
1. 完成所有更正后（如果有任何请求），并且知识库编写器和SME都批准该PR，则知识库编写器会将内容导入内部存储库并在内部合并内容。
1. [magento/知识库](https://github.com/magento/knowledge-base)存储库在20分钟内与内部存储库同步。
1. 同步存储库后，您的PR即会关闭，并且您会获得[贡献点](#contribution-points)。

有关贡献流的详细信息，请参阅[参与者指南](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md)。
有关模板、样式指南和格式设置指南，请参阅[文档](https://github.com/magento/knowledge-base/tree/main/docs)。

### 在Github上查找支持知识库文章文件

在支持知识库(KB)中，文章以节的形式组织，节以类别的形式排列。

例如，[如何订阅AdobeMagento状态更新](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md)文章属于操作方法类别中的“常规”部分。

您可以在文章页面的痕迹导航路径中查看部分和类别名称，请参阅下图：

![类别和章节痕迹导航](assets/breadcrumbs.png)

文章文件在[magento/知识库](https://github.com/magento/knowledge-base)存储库中的组织方式相同。
所有内容都存储在`src`文件夹中，其中包含类别文件夹和节的嵌套文件夹；文件名与文章标题一致或相似。

您还可以使用支持知识库文章中的一段文本作为搜索字符串在存储库中进行搜索。 当搜索返回包含此字符串的文件时，请确保选择属于右侧部分和类别的文件。

### 贡献点数

[magento/知识库](https://github.com/magento/knowledge-base)存储库与Magento社区工程集成，用于贡献点和支持。

请参阅[贡献点数](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md)文档，了解奖励点数的方式。
