---
title: 卸载非正则表达式重定向到Fastly而不是Nginx（路由）
description: 本主题针对您在云基础架构上的Adobe Commerce中将非正则表达式重定向卸载到Fastly而不是Nginx时可能遇到的典型重定向性能问题提供了解决方案。
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 卸载非正则表达式重定向到Fastly而不是Nginx（路由）

本主题针对您在云基础架构上的Adobe Commerce中将非正则表达式重定向卸载到Fastly而不是Nginx时可能遇到的典型重定向性能问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本） `Master/Production/Staging`环境利用Fastly

## 问题

在云基础架构上的Adobe Commerce中，无法在Nginx层执行大量非正则表达式重定向/重写，因此，可能会导致性能问题。

## 原因

`.magento/routes.yaml`目录中的`routes.yaml`文件为云基础架构上的Adobe Commerce定义了路由。

如果`routes.yaml`文件的大小为32KB或更大，则应将非正则表达式重定向/重写卸载到Fastly。

此Nginx层无法处理大量非正则表达式重定向/重写，否则会导致性能问题。

## 解决方案

解决方法是将这些非正则表达式重定向卸载到Fastly。 创建通用错误路径以重定向到Fastly。

以下步骤将详细介绍如何在Fastly上而不是Nginx上放置重定向。

1. 创建一个Edge词典。

   首先，您可以使用Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)中的[VCL代码片段来定义Edge词典。 这将包含重定向。

   对此有一些注意事项：

   * Fastly不能对字典条目执行正则表达式。 只是一模一样的。 有关这些限制的更多信息，请参阅[Fastly关于边缘词典限制的文档](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations)。
   * Fastly在单个词典中的限制为1000个条目。 Fastly可以扩大这一限制，但这引出了第三个警告。
   * 每当您更新条目并将更新的VCL部署到所有节点时，几何加载时间会随着词典的扩展而增加 — 这意味着，2000条条目的词典实际加载速度将比包含1000条条目的词典慢3到4倍。 但只有在部署VCL（更新词典或更改VCL函数代码）时，才会出现此问题。

     它不影响Fastly处理请求所需的时间；只影响Fastly推出新配置所需的时间。

     一般而言，配置更改平均需要几秒钟时间，通常不超过5-10秒。 因此，词典项目增加2倍需要30秒以上才能转出配置。 4倍的增长需要接近2分钟的时间。 这引出了第四个注意事项。

   * 边缘词典的词条数量严格限制为1万条。

   强烈建议整合您的重定向列表。 您可以使用多个字典，但请注意，您对VCL所做的任何更新都需要几分钟才能实际填充Fastly。

1. 将URL与字典进行比较。

   进行URL查找时，如果找到匹配项，则将进行比较以应用自定义错误代码。

   使用其他VCL代码片段向`vcl_recv`添加类似以下的内容：

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   在此，我们正在检查表条目中是否存在URL。 如果出现这种情况，我们将调用内部Fastly错误，并将来自表的重定向URL传递到该错误。

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
>如果您希望尝试执行所有这些步骤，强烈建议您设置Adobe Commerce暂存环境。 这样一来，你就可以对Fastly服务进行测试以确保一切如你所期望的那样运行。

如果您不想运行Adobe Commerce暂存环境，但希望了解这些重定向的外观，则可以直接在Fastly上设置暂存帐户。

## 相关阅读

* [Fastly VCL引用](https://docs.fastly.com/vcl/)
* [在我们的开发人员文档中配置路由](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html)。
* 在我们的开发人员文档中[设置Fastly](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。
* 在开发人员文档中的[VCL正则表达式备忘表](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet)。
