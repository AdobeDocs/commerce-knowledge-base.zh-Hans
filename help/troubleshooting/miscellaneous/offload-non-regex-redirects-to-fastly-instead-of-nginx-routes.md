---
title: '将非[!DNL regex]重定向卸载到 [!DNL Fastly] 而非 [!DNL Nginx] （路由）'
description: 本主题针对您在云基础架构上的Adobe Commerce中将非[!DNL regex]重定向卸载到 [!DNL Fastly] 而不是 [!DNL Nginx] 时可能遇到的典型重定向性能问题提供解决方案。
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# 将非[!DNL regex]重定向卸载到[!DNL Fastly]而不是[!DNL Nginx]（路由）

本主题针对您在云基础架构上的Adobe Commerce中将非[!DNL regex]重定向卸载到[!DNL Fastly]而不是[!DNL Nginx]时可能遇到的典型重定向性能问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本） `Master/Production/Staging`环境利用[!DNL Fastly]

## 问题

在云基础架构上的Adobe Commerce中，[!DNL Nginx]层无法执行大量非[!DNL regex]重定向/重写，因此可能会导致性能问题。

## 原因

`.magento/routes.yaml`目录中的`routes.yaml`文件为云基础架构上的Adobe Commerce定义了路由。

如果`routes.yaml`文件的大小为32KB或更大，则应将非[!DNL regex]重定向/重写卸载到[!DNL Fastly]。

此[!DNL Nginx]层无法处理大量非[!DNL regex]重定向/重写，否则会导致性能问题。

## 解决方案

解决方案是将这些非[!DNL regex]重定向卸载到[!DNL Fastly]。 创建通用错误路径以重定向到[!DNL Fastly]。

以下步骤将详细介绍如何在[!DNL Fastly]上而不是[!DNL Nginx]上放置重定向。

1. 创建一个Edge词典。

   首先，您可以使用Adobe Commerce[&#128279;](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)中的[!DNL VCL] 代码片段来定义Edge词典。 这将包含重定向。

   对此有一些注意事项：

   * [!DNL Fastly]无法在字典条目上执行[!DNL regex]操作。 只是一模一样的。 有关这些限制的更多信息，请参阅[[!DNL Fastly]的边缘词典限制文档](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations)。
   * [!DNL Fastly]在单个词典中的限制为1000个条目。 [!DNL Fastly]可以扩大此限制，但这会导致第三个注意事项。
   * 每当您更新条目并将更新[!DNL VCL]的条目部署到所有节点时，几何加载时间会随着词典的扩展而增加 — 这意味着，一个2000条条目的词典实际加载速度将比一个1000条目的词典慢3到4倍。 但只有在部署[!DNL VCL]（更新字典或更改[!DNL VCL]函数代码）时才会出现问题。

     它不影响[!DNL Fastly]处理请求所需的时间；它只影响[!DNL Fastly]推出新配置所需的时间。

     一般而言，配置更改平均需要几秒钟时间，通常不超过5-10秒。 因此，词典项目增加2倍需要30秒以上才能转出配置。 4倍的增长需要接近2分钟的时间。 这引出了第四个注意事项。

   * 边缘词典的词条数量严格限制为1万条。

   强烈建议整合您的重定向列表。 您可以使用多个字典，但请注意，您对[!DNL VCL]所做的任何更新都需要几分钟才能在[!DNL Fastly]中实际填充。

1. 将[!DNL URL]与字典进行比较。

   执行[!DNL URL]查找时，如果找到匹配项，则将进行比较以应用自定义错误代码。

   使用其他[!DNL VCL]代码片段向`vcl_recv`添加类似以下的内容：

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   在此，我们正在检查表条目中是否存在[!DNL URL]。 如果出现这种情况，我们将调用内部[!DNL Fastly]错误，并将来自表的重定向[!DNL URL]传递到该错误。

1. 管理重定向。

   当找到匹配项时，将执行为该`obj.status`定义的操作，在本例中为301永久移动重定向。

   在`vcl_error`中使用最终代码片段将301错误代码发送回客户端：

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   通过此块，我们正在检查从`vcl_recv`传入的错误代码是否匹配，如果匹配，我们将位置设置为传入的错误消息，然后将状态代码更改为301，并将消息更改为“已永久移动”。 此时，响应应准备好返回客户端。

### 暂存服务

>[!WARNING]
>
>如果您希望尝试执行所有这些步骤，强烈建议您设置Adobe Commerce暂存环境。 这样，您就可以针对[!DNL Fastly]服务运行测试，确保一切按预期运行。

如果您不想运行Adobe Commerce暂存环境，但希望了解这些重定向的外观，则可以直接在[!DNL Fastly]上设置暂存帐户。

## 相关阅读

* [[!DNL Fastly VCL] 引用](https://docs.fastly.com/vcl/)
* 在开发人员文档中[配置路由](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html)
* 在我们的开发人员文档中[设置 [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* 在开发人员文档中的[[!DNL VCL] 正则表达式备忘表](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
