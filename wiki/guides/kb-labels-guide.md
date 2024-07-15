---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# 知识库标签指南

本文档提供了向Adobe Commerce支持知识库中的文章添加标签的指南。
标签（也称为标记）可改善[Adobe Commerce支持知识库](https://support.magento.com/hc/en-us)中的搜索体验。
标签会添加到文章文件元数据部分的“标签”字段中，并以逗号分隔，逗号与下一个标签之间没有空格。
有关详细信息，请参阅[../../.github/CONTRIBUTING.md#metadata]。

## 一般规定

为每篇文章添加以下标签类型：

* 产品的标签。 （必填）
* 受影响版本的标签。 （必需，一般支持相关文章除外）
* 内容类型的标签。 （必填）
* 主要技术组件的标签。（如果适用）
* 正在疑难解答/描述的流程/功能的标签。 （如果适用）
* 正在修复/描述的问题标签。 （如果适用）

有关如何为每种标签类型定义标签的详细建议，请参阅以下部分。

## 产品标签

<table>
<tbody>
  <tr>
    <th>产品名称</th>
    <th>标签</th>
  </tr>
  <tr>
    <td>Adobe Commerce（所有部署方法） </td>
    <td>
    “Adobe Commerce，云基础架构，内部部署”
    </td>
  </tr>
  <tr>
    <td>云基础架构上的Adobe Commerce</td>
    <td>
      “Adobe Commerce，云基础架构”
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce内部部署</td>
    <td>“Adobe Commerce，内部部署”</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence(MBI)</td>
    <td>
        “Magento Business Intelligence，MBI”
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>适用于Adobe Commerce的B2B</td>
    <td>“B2B”</td>
  </tr>
  <tr>
    <td>Adobe CommercePWA</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia店面项目</td>
    <td>“威尼亚”</td>
  </tr>
  <tr>
    <td>Quality Patches Tool， QPT</td>
    <td>“Quality Patches Tool， QPT patches”</td>
  </tr>
  </tbody>
</table>

## 产品版本的标签

* 为每个Adobe Commerce版本添加单独的标签。 示例：“2.3.7”
* 请勿为间隔添加标签。
即，如果受2.3.0-2.3.5影响，则添加：“2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2”
不是“2.3.0-2.3.5”
* 不要添加带有.x的标签。示例： &quot;2.3.x&quot;

## 内容类型的标签（基于类别）

<table>
  <tbody>
    <tr>
      <th>类别</th>
      <th>标签</th>
    </tr>
    <tr>
      <td>最佳实践</td>
      <td>“最佳实践”（不是“最佳实践”或“最佳实践”）</td>
    </tr>
    <tr>
      <td>
        故障排除
      </td>
      <td>
      "疑难解答"
      </td>
    </tr>
    <tr>
      <td>操作方法</td>
      <td>“如何”</td>
    </tr>
    <tr>
      <td>常见问题解答</td>
      <td >“常见问题解答”</td>
    </tr>
  </tbody>
</table>

## 主要技术组件的标签

* 根据组件的正式命名使用大小写。
* 请勿使用同义词，即一个组件使用一个标签。
* 最好使用一个单词标签，但如果组件名称包含多个单词，请使用多个单词。 请勿添加问题描述。 也就是说，用“Elasticsearch”代替“Elasticsearch问题”。
* 如果内容仅与组件的特定版本相关，请添加包含名称+版本的标签。\
  示例：“Elasticsearch5”。 如果它与多个特定版本相关，请添加多个此类型的标签。 示例：“Elasticsearch5”、“Elasticsearch6”。 如果相关，请将“x”用于多个版本。 示例：“Elasticsearch2.x”

示例：

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* “Web设置向导”

## 正在疑难解答/描述的流程/功能标签

* 使用小写，但专有名词除外。
* 请勿使用同义词，即一个实体使用一个标签。
* 最好使用一个单词标签。 不要添加问题描述。 也就是说，应使用“数据库”而不是“数据库崩溃”。

示例： 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;部署&quot;
* &quot;批量更新&quot;

## 正在修复/描述的问题标签

* 使用小写，但专有名词除外。
* 请勿使用同义词，即一个实体使用一个标签。
* 最好使用一个单词标签。 请勿将错误消息转换为标签。

示例：

* &quot;site down&quot;
* “500错误”
* “卡住了cron”
