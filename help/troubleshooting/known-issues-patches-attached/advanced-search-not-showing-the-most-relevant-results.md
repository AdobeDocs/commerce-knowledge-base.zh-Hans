---
title: 高级搜索未显示最相关的结果
description: 本文为已知的Adobe Commerce问题提供了一个修补程序，在该问题中，高级搜索不会首先显示最相关的结果。
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 高级搜索未显示最相关的结果

本文为已知的Adobe Commerce问题提供了一个修补程序，在该问题中，高级搜索不会首先显示最相关的结果。

## 受影响的版本 {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce（所有部署选项） 2.x.x
* Magento Open Source2.x.x

## 问题 {#Advancedsearchnotshowingmostrelevantresults-Description}

高级搜索功能不会像快速搜索那样首先返回最相关的结果。 问题与所选的搜索引擎类型无关。

<u>要再现的步骤：</u>

1. 在店面，快速搜索“合身夹克”。
1. 请注意，“Orion Two-Tone Fitted Jacket”是第一个结果。
1. 转至高级搜索，然后在名称字段中搜索“Fitted Jacket”。

<u>预期结果：</u>

“Orion Two-Tone Fitted Jacket”是使用高级搜索时的第一个结果，是最相关的结果。

<u>实际结果：</u>

“Orion Two-Tone Fitted Jacket”不是第一个结果，尽管它是最相关的结果。

## 解决方案 {#Advancedsearchnotshowingmostrelevantresults-Solution}

要解决此问题，请应用本文附带的修补程序。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-7256\_EE\_2.1.7\_v1.composer.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

该修补程序将按高级搜索结果的相关性进行排序的实施添加为默认排序字段。

该修补程序与所有受影响的版本和版本兼容。

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
